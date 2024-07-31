**Timing Is Everything**

**Description**:
I was reading the recipe document for my famous 7 Layer Cake.

Lots of layers...like this challenge.

Author: r0m

**Walkthrough:**

I initially solved this challenge in the Open CTF because I somehow had the decimal representation of the first few characters of the flag format (SIVUSCG) memorized.

Based on the challenge name, it seems like it has something to do with the timings of the packets. First, I looked into the `frame.time` of the packets through Wireshark:
![image](https://github.com/user-attachments/assets/61d92f4d-d7d2-41e6-b07e-98b797e05624)

However, I quickly realized there was something going on in the `frame.time_delta`:
![image](https://github.com/user-attachments/assets/ee9eb751-c6d4-4384-b548-74dc11325ca5)
![image](https://github.com/user-attachments/assets/eb0a0411-fa3d-4ab3-84da-45fd2fa978b5)

These numbers were the flag in decimal!

Deciding to automate this in Bash (my personal favorite programming language), producing this oneliner:
```bash
for i in $(tshark -r timingiseverything.pcap -T fields -e frame.time_delta | cut -d "." -f 2 |awk '{ sub(/000000$/, "", $0); print }');do printf "\\$(printf '%03o' "$i")";done
```
Don't you just love oneliners?

**Flag**: `SIVUSCG{T1m1n9_15_3v3ryth1n9}`

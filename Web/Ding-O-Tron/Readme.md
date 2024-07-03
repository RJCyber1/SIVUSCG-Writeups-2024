#Ding-O-Tron

##Description
What came first? The ding...or the flag?

https://uscybercombine-s4-web-ding-o-tron.chals.io/

##Solution
When this challenge was live for the SIV USCG Open, I fell into a few rabbit holes.

I thought of first reaching 9000 dings (I sure was optimistic lol). In order to automate this, I took advantage of the `window.ding()` function and looped it like so:

```js
setInterval(function() {
  window.ding();
}, 800);
```

After reaching 9000 dings, however, I got the following message in my console: `[LOL] Did you think it would be that easy? Can you find my secret hidden function?`.

So, 9000 dings was obviously not the solve path.

Then, I tried reversing the ding.wasm file that was being run on the website. This was short-lived. I glanced back at the message I received after 9000 dings. It mentioned some `secret hidden function`. After some time, I ended up just typing in hidden into the console and the autocomplete showed the hidden function called `superSecretFunction_e5750a1a6c5e7767`.

After finding this function, it was just a matter of executing it.

![image](https://github.com/RJCyber1/SIVUSCG-Writeups-2024/assets/86359182/b0f845e1-0203-450c-9ac7-942f8a92deab)

Flag: `SIVUSCG{d1ng_d1ng_d1ng_d1ng}`

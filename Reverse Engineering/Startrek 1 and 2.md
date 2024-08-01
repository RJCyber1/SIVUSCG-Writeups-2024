**Startrek 1**

**Writeup**

The challenge supplies us with a binary, where our purpose is to get both starships to a certain location on the map (galaxy 100).

Here is the decompiled main function of the binary in `Pseudo C` in Binary Ninja:

```assembly
000013a1  int32_t main(int32_t argc, char** argv, char** envp)

000013a1  {
000013aa      void var_3e8;
000013aa      void* i = &var_3e8;
000013b1      void* fsbase;
000013b1      int64_t rax = *(uint64_t*)((char*)fsbase + 0x28);
000013e0      void s;
000013e0      *(uint32_t*)__builtin_memset(&s, 0, 0x330) = 0;  {  // {"o.2"}}
000013e6      int32_t var_70 = 0x64;
000013ed      int32_t var_6c = 5;
000013f4      int32_t forloopcounter = 2;
000013fb      int32_t var_280 = 0x5b;
00001405      int32_t padding = 0xf;
0000140f      int32_t var_34c = 0x29;
00001419      int32_t var_388 = 0x4b;
00001423      int32_t var_328 = 0x32;
0000142d      int32_t var_30c = 0x60;
00001437      int32_t var_2e8 = 0x52;
00001441      int32_t var_2c4 = 0x5e;
0000144b      int32_t var_2ac = 0x5f;
00001455      int32_t var_7c = 0xc;
0000145c      int32_t var_a4 = 0x43;
00001466      int32_t var_c0 = 0x3e;
00001470      int32_t var_d4 = 0x29;
0000147a      int32_t var_134 = 0x17;
00001484      int32_t var_148 = 0x1e;
0000148e      int32_t var_188 = 8;
00001498      int32_t var_1b0 = 3;
000014ac      int64_t var_3b0 = 1;
000014ed      int64_t rax_3 = ((COMBINE(0, 0x4f) / 0x10) * 0x10);
000014ed      
❓️00001504      while (i != (&var_3e8 - (rax_3 & 0xfffffffffffff000)))
00001504      {
00001506          i -= _init;
0000150d          *(uint64_t*)((char*)i + 0xff8) = *(uint64_t*)((char*)i + 0xff8);
❓️00001504      }
00001504      
00001521      void* rsp = ((char*)i - ((uint64_t)(rax_3 & 0xfff)));
00001521      
00001530      if (((uint64_t)(rax_3 & 0xfff)) != 0)
00001530      {
0000153b          void* rax_6 = ((((uint64_t)(rax_3 & 0xfff)) - 8) + rsp);
0000153e          *(uint64_t*)rax_6 = *(uint64_t*)rax_6;
00001530      }
00001530      
0000154d      uint64_t rax_10 = ((((char*)rsp + 7) >> 3) << 3);
0000154d      
0000165a      for (int32_t i_1 = 0; i_1 < forloopcounter; i_1 += 1)
0000165a      {
00001586          *(uint32_t*)((((int64_t)i_1) << 5) + rax_10) = (i_1 + 1);
000015a2          *(uint32_t*)(((((int64_t)i_1) << 5) + rax_10) + 4) = 0;
000015c6          *(uint32_t*)(((((int64_t)i_1) << 5) + rax_10) + 8) = var_6c;
000015e2          *(uint32_t*)(((((int64_t)i_1) << 5) + rax_10) + 0xc) = 0;
00001616          *(uint64_t*)(((((int64_t)i_1) << 5) + rax_10) + 0x10) = malloc((((int64_t)var_6c) << 2));
00001647          *(uint64_t*)(((((int64_t)i_1) << 5) + rax_10) + 0x18) = malloc((((int64_t)var_6c) << 2));
0000165a      }
0000165a      
00001674      int64_t var_58;
00001674      __builtin_memcpy(&var_58, "\x1c\x77\xf1\x50\x2a\x2c\xe9\x56\x1d\x0e\x98\x3d\x2c\x25\xe8\x4c\x5e\x69\xe3\x19\x4e\x03\x8f\x41\x0a\x39\x84\x0a\x20\x3f\xce\x04\x5c\x39\xa6\x50\x55\x46\x94\x5e\x1b\x6f\xee\x48\x1b\x33\xeb\x68", 0x30);
000016b4      char k = 0;
000016bb      int16_t format = 0;
000016c1      char var_59 = 0;
000016d1      srand(time(nullptr));
000016e0      puts("Captains Kirk and Spock both beg…");
00001a72      int32_t i_2;
00001a72      
00001a72      do
00001a72      {
000016e5          i_2 = 0;
000016e5          
00001a65          for (int32_t j = 0; j < forloopcounter; j += 1)
00001a65          {
0000171c              if (*(uint32_t*)(((((int64_t)j) << 5) + rax_10) + 8) > 0)
0000171c              {
0000173e                  i_2 += *(uint32_t*)(((((int64_t)j) << 5) + rax_10) + 8);
000017a5                  printf("\nStarship: %d\tCurrent Galaxy: …", ((uint64_t)*(uint32_t*)((((int64_t)j) << 5) + rax_10)), ((uint64_t)*(uint32_t*)(((((int64_t)j) << 5) + rax_10) + 4)), ((uint64_t)*(uint32_t*)(((((int64_t)j) << 5) + rax_10) + 8)));
000017b4                  puts("Preparing the ship for the next …");
000017e6                  int32_t var_3e0_1 = ((rand() % 6) + 1);
000017f1                  sleep(1);
00001800                  puts("Do you want to tell the Captain …");
0000181e                  __isoc99_scanf(&data_2288, &k);
0000181e                  
00001911                  while (k == 0x79)
00001911                  {
00001832                      puts("Choose a course heading for the …");
0000184d                      __isoc99_scanf(&data_22f4, &format);
00001852                      int32_t rax_86 = rand();
00001874                      int32_t rax_92 = ((rax_86 / 6) * 3);
0000188a                      sleep(1);
0000189e                      printf("The Starship is now headed in di…");
000018c0                      printf(&format, ((uint64_t)(((rax_86 - (rax_92 * 2)) + 1) * var_3e0_1)));
000018ca                      putchar(0xa);
000018d5                      var_3e0_1 = ((rax_86 - (rax_92 * 2)) + 1);
000018e5                      puts("Do you wish to modify the trajec…");
00001903                      __isoc99_scanf(&data_2288, &k);
00001911                  }
00001911                  
00001943                  jump(((((int64_t)j) << 5) + rax_10), var_3e0_1, &s);
00001990                  *(uint32_t*)(*(uint64_t*)(((((int64_t)j) << 5) + rax_10) + 0x10) + (((int64_t)*(uint32_t*)(((((int64_t)j) << 5) + rax_10) + 8)) << 2)) = var_3e0_1;
000019f0                  *(uint32_t*)(*(uint64_t*)(((((int64_t)j) << 5) + rax_10) + 0x18) + (((int64_t)*(uint32_t*)(((((int64_t)j) << 5) + rax_10) + 8)) << 2)) = *(uint32_t*)(((((int64_t)j) << 5) + rax_10) + 4);
000019f0                  
00001a13                  if (*(uint32_t*)(((((int64_t)j) << 5) + rax_10) + 4) >= var_70)
00001a13                  {
00001a2f                      *(uint32_t*)(((((int64_t)j) << 5) + rax_10) + 8) = 0;
00001a4f                      *(uint32_t*)(((((int64_t)j) << 5) + rax_10) + 0xc) = 0xbaadd00d;
00001a13                  }
0000171c              }
00001a65          }
00001a72      } while (i_2 != 0);
00001a7a      int32_t var_3d8 = 0;
00001a7a      
00001ac7      for (int32_t i_3 = 0; i_3 < forloopcounter; i_3 += 1)
00001ac7      {
00001aae          if (*(uint32_t*)(((((int64_t)i_3) << 5) + rax_10) + 0xc) != 0)
00001ab0              var_3d8 += 1;
00001ac7      }
00001ac7      
00001ad2      if (var_3d8 != forloopcounter)
00001dfd          puts("You failed to guide both ships t…");
00001ad2      else
00001ad2      {
00001ae2          puts("The Architects are impressed by …");
00001af1          int64_t var_3c8_1 = '%#\"\x84\xe4\x9c\xf2\xcb';
00001af1          
00001b5c          for (int32_t i_4 = 0; i_4 <= 0x333; i_4 += 1)
00001b43              var_3c8_1 = (((uint64_t)*(uint8_t*)(&s + ((int64_t)i_4))) ^ (0x100000001b3 * var_3c8_1));
00001b43          
00001b5e          int64_t var_3c0_1 = 0;
00001b5e          
00001c13          for (int32_t i_5 = 0; i_5 < var_6c; i_5 += 1)
00001c13          {
00001bf8              int32_t rax_196 = ((*(uint32_t*)((((int64_t)i_5) << 2) + *(uint64_t*)(rax_10 + 0x38)) * *(uint32_t*)((((int64_t)i_5) << 2) + *(uint64_t*)(rax_10 + 0x30))) ^ (*(uint32_t*)((((int64_t)i_5) << 2) + *(uint64_t*)(rax_10 + 0x10)) * *(uint32_t*)((((int64_t)i_5) << 2) + *(uint64_t*)(rax_10 + 0x18))));
00001bfc              var_3c0_1 = ((var_3c0_1 << 0xa) | ((int64_t)rax_196));
00001c13          }
00001c13          
00001c5d          for (int32_t i_6 = 0; i_6 < var_6c; i_6 += 1)
00001c5d          {
00001c33              int64_t rax_200 = _pdep_u64(var_3c0_1, var_3c8_1);
00001c3f              var_3c0_1 <<= 1;
00001c46              var_3c8_1 = !(rax_200);
00001c5d          }
00001c5d          
00001cb7          for (int32_t i_7 = 0; i_7 <= 5; i_7 += 1)
00001ca3              &var_58[((int64_t)i_7)] ^= var_3c8_1;
00001ca3          
00001deb          for (int32_t i_8 = 0; i_8 < var_6c; i_8 += 1)
00001deb          {
00001d0c              int32_t rax_225 = (*(uint32_t*)((((int64_t)((var_6c - 1) - i_8)) << 2) + *(uint64_t*)(rax_10 + 0x30)) * *(uint32_t*)((((int64_t)((var_6c - 1) - i_8)) << 2) + *(uint64_t*)(rax_10 + 0x10)));
00001d0c              
00001dd5              for (int32_t j_1 = 0; j_1 < rax_225; j_1 += 1)
00001dd5              {
00001d24                  char rax_226 = var_58;
00001d24                  
00001d6b                  for (int64_t k_1 = 0; k_1 <= 0x2e; k_1 += 1)
00001d59                      *(uint8_t*)(k_1 + &var_58) = *(uint8_t*)(&var_58 + (k_1 + 1));
00001d59                  
00001d74                  int64_t var_30_1;
00001d74                  *(uint8_t*)((char*)var_30_1)[7] = rax_226;
00001d8a                  var_58 ^= *(uint8_t*)(&var_58 + ((int64_t)rax_225));
00001da8                  *(uint8_t*)(&var_58 + ((int64_t)rax_225)) ^= var_58;
00001dbf                  var_58 ^= *(uint8_t*)(&var_58 + ((int64_t)rax_225));
00001dd5              }
00001deb          }
00001ad2      }
00001ad2      
00001e0e      *(uint64_t*)((char*)fsbase + 0x28);
00001e0e      
00001e17      if (rax == *(uint64_t*)((char*)fsbase + 0x28))
00001e23          return 0;
00001e23      
00001e19      __stack_chk_fail();
00001e19      /* no return */
000013a1  }
```

Note that I renamed a variable to `forloopcounter` in order to better understand the code. 

Here is a brief summary of the above code:
The code basically uses a seeded random in the context of the libc (libc.so.6) in order to pick where to navigate the ships. The script loops twice in a `for` loop for both starship. If both ships are unable to reach the destination, the code ends and does not display the flag.

Firstly, I thought I would be able to patch the binary somehow in order to get the code to get both starships to 100. This rabbit hole took quite some time to overcome. However, I quickly realized that this would not work because it would not decrypt the flag properly. 
I came to the conclusion that this would end up involving Breadth First Search (BFS) to navigate the map, using the jumps and slipstreams to reach galaxy 100.

I believe the second challenge would also end up being BFS with the jumps and slipstreams (with the goal being 1600 this time). However, I was unable to get the code to work in order to navigate the starships to the goal. This was probably due to errors in my dictionaries for the wormholes and slipstreams or the way the BFS was implemented in the context of this binary.

Overall, this challenge was a fun way to learn more about the applications of BFS and how they can be used to find moves to solve a game.

After the Open CTF, I saw someone link this stackoverflow response that implemented BFS on Snakes and Ladders in order to figure out the minimum number of moves (jumps) to win the game and thought it was quite applicable to our case: https://stackoverflow.com/questions/18318780/minimum-steps-to-win-snake-ladder/18322848#18322848

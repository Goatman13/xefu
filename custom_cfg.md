## Overview
Custom config file is scene implementation of what normally xefutitle files do. It allows user to inject custom configuration for their games and hopefully fix bugs in emulation for said games.

## Custom config file structure
File is simple binary named after game id. For example Kung Fu Chaos config name is 4D530031.bin (ID in upper case, bin lower case).

Structure is very simple, you can split it into 34 4 bytes fields where first 14 fields are cfg1 - cfg14 values, and later 20 fields are for data for more advanced cfg8/10/12/14 commands. Data is big endian.
![cust](https://github.com/user-attachments/assets/f1dd4d28-3a12-4a11-b87b-7b456e2e642b)

Example config for Kung Fu Chaos with cfg1 set to 02000000, cfg3 set to 000000D8, cfg7 set to 4 and cfg8 set to pointer 82168CC8 (0x38 in our configs, check bugs/limitations tab) with additional data. Other cfg values are set to 0.
![kfc](https://github.com/user-attachments/assets/851bc6dd-138f-46a5-93f8-dd58611dc683)

## Bugs / Limitations
* Currently supported configs are limited to 0x88 bytes, where 0x38 is taken by cfg1 - cfg 14 fileds. This leave only 0x50 bytes for more advanced cfg8/10/12/14. At first it should be no issue, but later when more info will be figured out it might be too small space to fit what's needed.
* Configs are always loaded at 0x82168C90 address, cfg 8/10/12/14 pointers need to be prepared remembering that "free space" in config starts at 0x82168C90 + 0x38 (0x82168CC8). Few translated official configs will be posted to show what this mean.
* There is no region check, game version check, or any check, beside game ID. There was no space to implement that in xefu file, and it would additionally take valuable space for config data. This shouldn't be an issue for cfg 1-6, and 9/10 as they are generally not Original Xbox memory address dependent. For the rest user will need to figure out his game version and use matching region config. 

## Overview
Custom config files are community implementations of what xefutitle files do. They allow users to inject custom configurations for their games and hopefully fix bugs in emulation for said games.

## Custom config file structure
The file is simple binary named after the game ID. For example, Kung Fu Chaos's config name is 4D530031.bin (ID in upper case, bin lower case).

The structure is very simple, you can split it into 34 4-byte fields where first 14 fields are cfg1 - cfg14 values, and next 20 fields are for data for more advanced cfg8/10/12/14 commands. Data is big endian.
![cust](https://github.com/user-attachments/assets/f1dd4d28-3a12-4a11-b87b-7b456e2e642b)

Example config for Kung Fu Chaos with cfg1 set to 02000000, cfg3 set to 000000D8, cfg7 set to 4 and cfg8 set to pointer 82168CC8 with additional data (0x38 in our configs, check bugs/limitations tab). Other cfg values are set to 0.
![kfc](https://github.com/user-attachments/assets/851bc6dd-138f-46a5-93f8-dd58611dc683)

## Bugs / Limitations
* Currently supported configs are limited to 0x88 bytes, where 0x38 is taken by cfg1 - cfg 14 fields. This leaves only 0x50 bytes for more advanced cfg8/10/12/14 settings. At first it should be no issue, but later when more info will be figured out it might be too small of a space to fit what's needed.
* Configs are always loaded at 0x82168C90 address, cfg 8/10/12/14 pointers need to be prepared while having in mind that "free space" in config starts at 0x82168C90 + 0x38 (0x82168CC8). A few translated official configs will be posted to show what this means.
* There is no region check, game version check, or any check, beside game ID. There was no space to implement that in the xefu file, and it would additionally take valuable space for config data. This shouldn't be an issue for cfg 1-6, and 9/10 as they are generally not Original Xbox memory address dependent. For the rest, users will need to figure out their game version and use a matching region config. 

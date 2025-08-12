## Overview
Custom config file is scene implementation of what normally xefutitle files do. It allows user to inject custom configuration for their games and hopefully fix bugs in emulation for said games.

## Custom config file structure

## Bugs / Limitations
* Currently supported configs are limited to 0x88 bytes, where 0x38 is taken by cfg1 - cfg 14 fileds. This leave only 0x50 bytes for more advanced cfg8/10/12/14. At first it should be no issue, but later when more info will be figured out it might be too small space to fit what's needed.
* Configs are always loaded at 0x82168C90 address, cfg 8/10/12/14 pointers need to be prepared remembering that "free space" in config starts at 0x82168C90 + 0x38 (0x82168CC8). Few translated official configs will be posted to show what this mean.
* There is no region check, game version check, or any check, beside game ID. There was no space to implement that in xefu file, and it would additionally take valuable space for config data. This shouldn't be an issue for cfg 1-6, and 9/10 as they are generally not Original Xbox memory address dependent. For the rest user will need to figure out his game version and use matching region config. 

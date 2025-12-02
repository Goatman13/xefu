## Overview
Config related to some kind of Xbox memory read/write (not hardware MMIO, but rather RAM). When enabled, performs check if requested xb1 address is in xbe or xb1krnl .text segment range. Config is a 32-bit big endian integer, but only values 0x00000000 and 0x00000001 are valid. This command require bit 0x00010000 of cfg1 to be active.

## Known Values
* 0x00000000   = Default value (this will crash emulator if config is activated by cfg1)
* 0x00000001   = Enable check
* other values = Undefined behavior (this will crash emulator or do random thing if config is activated by cfg1)

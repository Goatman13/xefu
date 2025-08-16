## Overview
Config related to some kind of Xbox memory read (not hw mmio, rather ram). When enabled perform some additional check to sse if "something" is in "range". Might be pipeline timing related, or cache related. Config is a 32 bit big endian integer, but only values 0x00000000 and 0x00000001 are valid. This command require bit 0x00010000 of cfg1 to be active.

## Values
* 0x00000000   = Default value (this will crash emulator if config is activated by cfg1)
* 0x00000001   = Enable additional check.
* other values = Undefined behavior (this will crash emulator or do random thing if config is activated by cfg1)

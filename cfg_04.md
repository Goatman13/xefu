## Overview
The overall kernel stack size limit, measured in bytes, sets the cap on the total kernel stack size for all created x86 threads. Config is a 32-bit big endian integer. This command requires bit 0x00000008 of cfg1 to be active.

## Known Values
* Default value is 0x00100000

## Overview
Set x86 threads count limit (eg. Created by xb1krnl export PsCreateSystemThread/PsCreateSystemThreadEx). Since default limit is rather low 0x30 (48), some games might need this number to be higher. Config is a 32-bit big endian integer. This command requires bit 0x00000010 of cfg1 to be active.

## Known Values
* Default value is 0x00000030

## Overview
Filesystem (called internally Fsdx) related settings. Config is a 32-bit big endian bitfield, but only bits 0x000001FF are actively used by emulator. Instead of describing bits as 0..31 or 1 << x, I decided to use raw values here for clarity.
When we want to activate more than one field at a time, just add the values for them. For example, want field 0x02000000 and field 0x00000001 active? Use value 0x02000001. Just remember that values here are hexadecimal, 0x00000004 + 0x00000008 = 0x0000000C, not 0x00000012. Windows calculator in programmer hex mode might be helpful here for newcomers.

## Known Values
* 0x00000001 = Force xb1krln function IoParseDevice to always set `fileObject->Flags |= FO_SYNCHRONOUS_IO` if `DesiredAccess & GENERIC_WRITE` set.
* 0x00000002 = Force xb1krln function IoParseDevice to always set `fileObject->Flags |= FO_SYNCHRONOUS_IO` if `DesiredAccess & GENERIC_READ` set.

## More Info
### 0x00000001 and 0x00000002
There’s a bit more to it, but generally those configurations ensure that files (and devices?) opened by NtCreateFile are read/write in synchronous mode. It’s worth noting that despite its name, NtCreateFile is also used for opening existing files.

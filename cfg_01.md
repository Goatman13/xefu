## Overview
General config with many options. Config is a 32 bit big endian bitfield. Instead of describing bits as 0..31 or 1 << x, I decided to use raw values here for better understanding.
When we want activate more than one field at once, just add values for them. For example want field 0x02000000 and field 0x00000001 active? Use value 0x02000001. Just remember that values here are hexadecimal, 0x00000004 + 0x00000008 = 0x0000000C, not 0x00000012. Windows calculator in programmer hex mode might be helpful here for newcommers.

## Values
* 0x00000001 = emu quit/reset related. When enabled XamLoaderSetLaunchData(data, 0x3FC) is called on exit with data[0] = 2 and data[1] = 6
* 0x00000004 = unknown, x86 pipe/ x86 rec related
* 0x00000008 = enable cfg4, without it cfg4 is not used regardless of its value.
* 0x00000010 = enable cfg5, without it cfg5 is not used regardless of its value.
* 0x00000040 = force secondary dispatch
* 0x00010000 = enable cfg6, without it cfg6 is not used regardless of its value.
* 0x00080000 = File system related, when enabled skips precompiled function FsdxMarkBufferDirty.
* 0x00400000 = unknown, seems to alter cfg9/cfg10 behavior
* 0x00800000 = unknown, cfg9/cfg10 related
* 0x02000000 = Enable Altivec "java mode" (set vscr bit NJ [bit111] to 0), basically makes Altivec IEEE compilant. It's very important for this bit to be always enabled. No idea why there is even an option to disable it for x86 emulator...

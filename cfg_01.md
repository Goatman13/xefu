## Overview
General config with many options. The config is a 32-bit big endian bitfield. Instead of describing bits as 0..31 or 1 << x, I decided to use raw values here for clarity.
When we want to activate more than one field at a time, just add the values for them. For example, want field 0x02000000 and field 0x00000001 active? Use value 0x02000001. Just remember that values here are hexadecimal, 0x00000004 + 0x00000008 = 0x0000000C, not 0x00000012. Windows calculator in programmer hex mode might be helpful here for newcomers.

## Values
* 0x00000001 = Emulator quit/reset related. When enabled, XamLoaderSetLaunchData(data, 0x3FC) is called on exit with data[0] = 2 and data[1] = 6
* 0x00000002 = Start emulation with cr1:lt = 0 (cr1 decides about dispatcher behavior when emulation starts).
* 0x00000004 = Unknown, x86 pipe/ x86 rec related
* 0x00000008 = Enable cfg4, without it cfg4 is not used regardless of its value.
* 0x00000010 = Enable cfg5, without it cfg5 is not used regardless of its value.
* 0x00000040 = Force secondary dispatch, also start emulation with cr1:eq = 1 (cr1 decides about dispatcher behavior when emulation starts).
* 0x00000080 = Start emulation with cr1:gt = 1 (cr1 decides about dispatcher behavior when emulation starts).
* 0x00010000 = Enable cfg6, without it cfg6 is not used regardless of its value.
* 0x00080000 = File system related, when enabled skips precompiled function FsdxMarkBufferDirty.
* 0x00400000 = Unknown, seems to alter cfg9/cfg10 behavior
* 0x00800000 = Unknown, cfg9/cfg10 related
* 0x02000000 = Enable Altivec "java mode" (set vscr bit NJ [bit111] to 0), basically makes Altivec IEEE compilant. It's very important for this bit to be always enabled. No idea why there is even an option to disable it for an x86 emulator...
* 0x04000000 = Set Floating Point operations to use round to zero mode instead of round to nearest (set RN bits in FPSCR to 01). Affects only operations done on fpu registers, not altivec.

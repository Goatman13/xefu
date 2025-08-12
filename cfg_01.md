## Overview
General config with many options, not bounded to any typical part of emulation. Config is a 32 bit big endian bitfield. Instead of describing bits as 0..31 or 1 << x, I decided to use raw values here for better understanding.
When we want activate more than one field at once, just add values for them. For example want field 0x02000000 and filed 0x00000001 active? Use value 0x02000001.

## Values
* 0x00000001 = emu quit/reset related. When enabled XamLoaderSetLaunchData(data, 0x3FC) is called on exit with data[0] = 2 and data[1] = 6
* 0x00000004 = unknown, x86 pipe/ x86 rec related
* 0x00000008 = enable cfg4, without it cfg4 is not used regardless of its value.
* 0x00000010 = enable cfg5, without it cfg5 is not used regardless of its value.
* 0x00000040 = if "something" then force secondary dispatch (whatever it means...)
* 0x00010000 = enable cfg6, without it cfg6 is not used regardless of its value.
* 0x00080000 = May be filesystem related. Performs some check for precompiled functions FsdxMarkBufferDirtyStart/FsdxMarkBufferDirtyEnd. // todo
* 0x00400000 = alter cfg9/cfg10 behavior (require 0x00800000 to be active) - **wrong, check legacy of kain**
* 0x00800000 = enable cfg9/cfg10

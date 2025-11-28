## Overview
General config with many options. The config is a 32-bit big endian bitfield. Instead of describing bits as 0..31 or 1 << x, I decided to use raw values here for clarity.
When we want to activate more than one field at a time, just add the values for them. For example, want field 0x02000000 and field 0x00000001 active? Use value 0x02000001. Just remember that values here are hexadecimal, 0x00000004 + 0x00000008 = 0x0000000C, not 0x00000012. Windows calculator in programmer hex mode might be helpful here for newcomers.

## Values
* 0x00000001 = Emulator quit/reset related. When enabled, XamLoaderSetLaunchData(data, 0x3FC) is called on exit with data.source = 2(SOURCE_XBOX) and data.reason = 6
* 0x00000002 = Start emulation with cr1:lt = 0 (cr1 decides about dispatcher behavior when emulation starts).
* 0x00000004 = Unknown, x86 pipe/ x86 rec related
* 0x00000008 = Enable cfg4, without it cfg4 is not used regardless of its value.
* 0x00000010 = Enable cfg5, without it cfg5 is not used regardless of its value.
* 0x00000040 = Force secondary dispatch, also start emulation with cr1:eq = 1 (cr1 decides about dispatcher behavior when emulation starts).
* 0x00000080 = Start emulation with cr1:gt = 1 (cr1 decides about dispatcher behavior when emulation starts).
* 0x00010000 = Enable cfg6, without it cfg6 is not used regardless of its value.
* 0x00020000 = Skip PageFrame->Busy.LockCount value update in xb1krnl MmLockUnlockBufferPages function.
* 0x00040000 = Enable precompiled function FsdxTouchBuffer. This function is used by xb1krnl but can be called from rcompiled code too.
* 0x00080000 = File system related, when enabled skips precompiled function FsdxMarkBufferDirty.
* 0x00100000 = Skip specific data sequence.
* 0x00400000 = Unknown, seems to alter cfg9/cfg10 behavior
* 0x00800000 = Unknown, cfg9/cfg10 related
* 0x02000000 = Enable Altivec "java mode" (set vscr bit NJ [bit111] to 0), basically makes Altivec IEEE compilant. It's very important for this bit to be always enabled. No idea why there is even an option to disable it for an x86 emulator...
* 0x04000000 = Set Floating Point operations to use round to zero mode instead of round to nearest (set RN bits in FPSCR to 01). Affects only operations done on fpu registers, not altivec.
* 0x08000000 = Use 32 bit ppc fpu math instead of doubles for selected x87 opcodes. Eg. Use ppc fadds instead of ppc fadd during x87 fadd recompilation.
* 0x10000000 = Skip opcode vpcext 5, 4 injection. This in turn skips one case of precompiled function "TitleGlue".

## More Info
### 0x00100000
Skip recompilation of aligment/data hex sequence related to exception handling.<br>
Emulator search for this hex sequence: `56 43 32 30 58 43 30 30 55`. Eventually preceded by byte(s) 0x00, 0x90, or 0xCC. Then skip all that and do not treat it as a valid x86 code.

This "code" seems to be misinterpreted string "VC20XC00U". While it can be found in many games, MS used this command only for few of them (Amped, Soul Calibur 2, Crimson Skies: High Road to Revenge, few more). It's unclear why only those games required it.

### 0x00040000
Enable precompiled function FsdxTouchBuffer. This function is used by xb1krnl but can be called from rcompiled code too.<br>
The enabled function simply touches the requested memory range by loading a byte into void, using 0x1000 byte sized pages in PPC code. This most likely load data into ppc cache or eventually simulates cycles that will be burned during that operation on original xbox.

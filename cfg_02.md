## Overview
Gpu and video config with many options. Config is a 32 bit big endian bitfield. Instead of describing bits as 0..31 or 1 << x, I decided to use raw values here for better understanding.
When we want activate more than one field at once, just add values for them. For example want field 0x02000000 and field 0x00000001 active? Use value 0x02000001. Just remember that values here are hexadecimal, 0x00000004 + 0x00000008 = 0x0000000C, not 0x00000012. Windows calculator in programmer hex mode might be helpful here for newcommers.

## Values
* 0x00000004 = skip D3DQuery_Issue and D3DQuery_GetData
* 0x00000008 = arithmetically "or" 0x100 to 4th param for function D3D::CMicrocodeBuilder::Microcode::DeclareInterpolatorSemantic (few other dependencies need to be fullfiled to hit that code path)
* 0x00000100 = interlaced/progressive mode related
* 0x00000200 = Set widescreen mode

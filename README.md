# ghidra_psx_ldr
Sony Playstation PSX executables loader for GHIDRA

Video tutorial on how to deal with overlays: https://youtu.be/DuQQfjTkkQc

# Building
* Install `GhidraDev` plugin into Eclipse
* Add your Ghidra installation dir
* Import this repository into Eclipse
* Do GhidraDev -> Link Ghidra...
* Press GhidraDev -> Export -> Ghidra module extension...
    
# Installation
* Open Ghidra, go to File -> Install Extensions... and select the .zip file generated by the previous step

# Analysing PSYQ LIBs and OBJs
* In case you have a directory with OBJ-files extracted from a LIB-file, create an empty `PSYQ_LIBNAME_XXX` file, where `LIBNAME` is your LIB-file name (for ex. `LIBSND`) and `XXX` is PSYQ version number according to [this list](https://github.com/lab313ru/psx_psyq_signatures).
* In case you want to batch-import all OBJ-files for a LIB-file or import a standalone OBJ-file (like `8MBYTE.OBJ`), create an empty `PSYQ_XXX` file, where `XXX` is PSYQ version number according to [this list](https://github.com/lab313ru/psx_psyq_signatures).

# Moving from projects created without `ghidra_psx_ldr`
- On your project: `Set Language`, choose `PSX`, `Yes`, `Yes`, `OK`
- Script Manager->`PSX GTE` folder, run `CreateGteMacSegment` script
- Reanalyze

# Decompiling GTE macroses in your old projects
- Reanalyze. It will create a special segment with GTE macro handlers.
If you have some Ghidra project which has been created before `01/22/2022`, in order to decompile any GTE related stuff it requires to undefine (*select disasm lines and press `C`*) and disassemble (*press `D`*) instructions again, because Ghidra's decompiler uses disasm and Pcodes information stored in a project.

# Fixing a problem with "`psyq/xx`" cannot be found:
- Go to `Edit`->`Options for 'blabla'`->`Program information`->`PsyQ Version` field
- Add `.0` there
![Screen8](/imgs/screen8.png?raw=true)

# Patches format ([example here](https://github.com/lab313ru/psx_psyq_signatures/blob/main/patches.json))

* `~` - is for replacing some pattern in a signature. check field is the original bytes in the signature to compare with
* `+` - is for adding some pattern in a signature
* `-` - is for removing some pattern from a signature

! `pos` fields are for the original signature. you should not add appended or removed sizes to them

# Screenshots

![Screen1](/imgs/screen1.png?raw=true)
![Screen7](/imgs/screen7.png?raw=true)
![Screen4](/imgs/screen4.png?raw=true)
![Screen5](/imgs/screen5.png?raw=true)
![Screen6](/imgs/screen6.png?raw=true)


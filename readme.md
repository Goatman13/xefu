## Xbox 360 XeFu Research
This repository documents the internal workings of the Xenon Fusion (XeFu) emulator config files for running original Xbox games on Xbox 360. The emulator files make use of "xefutitle" files that contain per-title configuration sets of 14 configurations (cfgs).

## Config Research

### cfgXX
cfgXX.md files contain info about the specified cfg.

### txt_config_dumps
Configs from officially released xefu files dumped in txt form. For learning purposes.

### xefutitle7_dump
Configs from xefu7 dumped in binary form, useful for testing on different games by just changing title ID.

&nbsp;

## Custom Configs

### Configs folder
The Configs folder found in this repo are ready-to-go configs that can be dropped into `hddx:\Compatibility\Configs\` on your console.

### custom_cfg.md
General info about how to create custom config files to be used with config_loader_xefu7.xex and how they are implemented.

### cfgs_examples
Configs which can be used as a base for creating new ones. Please keep in mind that most of them have set default values, so they will likely do nothing without editing said values.

&nbsp;

## Using Custom Configs

### Xefu Spoofer
The easiest way to enable config loading is to download Xefu Spoofer and the latest hacked xefu pack. "Xefu7 with Config Loader" will then be an option in Xefu Spoofer and any config files found in `hddx:\Compatibility\Configs\` with a matching title ID will automatically be loaded when launching a title. More information on Xefu Spoofer can be found on [ConsoleMods.org](https://consolemods.org/wiki/Xbox_360:Original_Xbox_Games_Compatibility_List).

### Without Xefu Spoofer
Download the latest [hacked xefu pack](https://consolemods.org/wiki/File:Hacked_Xefu_Pack.zip), rename config_loader_xefu7.xex to xefu7.xex, and replace `hddx:\Compatibility\xefu7.xex` with your renamed file. Any config files found in `hddx:\Compatibility\Configs\` with a matching title ID will automatically be loaded when launching a title.

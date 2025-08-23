## Xbox 360 XeFu Research
This repository documents the internal workings of the Xenon Fusion (XeFu) emulator config files for running original Xbox games on Xbox 360. The emulator files make use of "xefutitle" files that contain per-title configuration sets of 14 configurations (cfgs).

### cfgXX
cfgXX.md files contain info about the specified cfg.

### txt_config_dumps
Configs from officially released xefu files dumped in txt form. For learning purposes.

### xefutitle7_dump
Configs from xefu7 dumped in binary form, useful for testing on different games by just changing title ID.

&nbsp;

## Custom Configs

### custom_cfg.md
General info about how to create custom config files to be used with config_loader_xefu7.xex and how they are implemented.

### cfgs_examples
Configs which can be used as a base for creating new ones. Please keep in mind that most of them have set default values, so they will likely do nothing without editing said values.

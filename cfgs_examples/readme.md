## Info
Configs to be used as a base for new configs. They also show where respective commands are placed inside bin files. Remember to rename them to <game-id>.bin for your game.

### cfg_base_default
Without any mods, this config is used by xefu7 when a matching title ID is not found in database. All other configs with cfg_base_default in the name include those default settings.
### cfg_base_default_widescreen
Default config with enabled widescreen (if game don't support widescreen, you need a widescreen patch or everthing will be just stretched).
### cfg_base_default_plus_cfg4
Enable cfg4 edit 4 bytes hex value at address 0x0C to modify cfg4 value. Without this addition, the config is set to the default value used in emulator (it will do nothing without editing).
### cfg_base_default_plus_cfg5
Enable cfg5 edit 4 bytes hex value at address 0x10 to modify cfg5 value. Without this addition, the config is set to the default value used in emulator (it will do nothing without editing).
### cfg_base_default_plus_cfg4_and_cfg5
Enable cfg4 and cfg5, read description above.
### cfg_base_default_plus_cfg6
Enable cfg6. The only supported value for cfg6 is used here, no need to change anything here. It either do something in the game, or not.
### cfg_base_default_plus_cfg9_and_cfg_10
Enable cfg13/cfg14 for single entry. Replace 3 x 4 bytes entries at 0x3C/0x40/0x44 to change ".text" segment recompilation options. Change .text string at 0x48 if you target a different segment.
### cfg_base_default_plus_cfg13_and_cfg_14
Enable cfg13/cfg14 for single entry. Replace 3 x 4 bytes entries at 0x38/0x3C/0x40 to memory addresses to make a config for your game.
### 4D530031.bin
This config is a backport of the official Kung Fu Chaos config from xefutitle2019, just to show how it changes.

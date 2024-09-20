# BeachLife HD Patch
With this patched executable the game is now rendering in native 1920x1080.

## Disclaimer
I am not associated with Eidos Interactive in any way. All rights belong to them.

## Recommendations
It is highly recommended that you install the dxwrapper dlls for better performance and v-sync support. You only need the main dxwrapper and ddraw dlls. A configured dxwrapper.ini is provided in the repository.
https://github.com/elishacloud/dxwrapper

## Installation
- Replace the main executable and ini file
- Install dxwrapper and ini file
- Enjoy!
### If using the latest commit
WIP: Replace the files from the data directory. Possibly unfinished, buggy or crashing

## Known issues
- Main menu is rendering in FullHD. The background bitmaps had to be extended otherwise it crashes. I tried my best, but i am by no means a graphics designer.
- Only the game is rendered at higher resolution, the assets are still the same quality.
- Only tested on a FullHD monitor. Thanks to dxwrapper it should scale the image accordingly at any higher resolution.
- Do not try to change the resolution in-game.

## Heads-up for reversing
The IDA database is provided. Note that the intro video cannot be played during debugging. Disable it in Data/Script/GameParameters.pis (Text File). Also the patched version does not work inside a VM because the Microsoft Basic Display Adapter only supports a maximum resolution of 1280x1050. The display initialisation IDirectDraw7::setDisplayMode() will fail. You have to use a "real" GPU driver. 
### Game script files
The UI and probable many mechanics are defined via .ble file inside Data/Script/. These files are "encrypted" (byte-wise not) and are basically text definitions. The provided bleCoder.jar programm can en-/decode these files.
### Multimedia
A wrong media format crashes the game, otherwise it will be rendered appropriately.
#### Video 
```ffmpeg -i .\SomeVideo.mpg -c:v mpeg1video -c:a mp2 -ar 44100 -b:a 224k CompatibleVideo.mpg```
#### Screens
TGA 24bit 256-Indexed, In GIMP remove the alpha channel to get 24bit. Be aware that the default in GIMP for indexed Color is 255 not 256. After saving check with a hex editor for the correct header:

| Offset Byte address | Value | Meaning |
| :---------------- | :------: | ----: |
| 05       |   0x00  | Lower byte color palette size |
| 06         |   0x01  | Higher byte color palette size (256) |
| 07   |  0x18  | 24bit color |

Sometimes GIMP doesn't export the file correctly, in that case, save as png, close GIMP, open, load png and try exporting again.

## Credits
Thanks to the team at elishacloud for developing the dxwrapper and to my friends for giving me new inspirations when i was stuck reverse engineering. And of course all the credits to the people at Eidos and DeepRed for developing the game in the first place.

  

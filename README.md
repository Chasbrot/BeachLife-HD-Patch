# BeachLife HD Patch
With this patched executable the game is now rendering in native 1920x1080.

## Disclaimer
I am not associated with Eidos Interactive in any way. All rights belong to them.

## Recommendations
It is highly recommended that you install the dxwrapper dlls for better performance and v-sync support. You only need the main dxwrapper and ddraw dlls. A configured dxwrapper.ini is provided in the repository.
https://github.com/elishacloud/dxwrapper

## Installtion
- Replace the main executable and ini file
- Install dxwrapper and ini file
- Enjoy!

## Known issues
- Main menu is only rendering in 800x600 (WIP)
- Only the game is rendered at higher resolution, the assets are still the same quality.
- Only tested on a FullHD monitor. Thanks to dxwrapper it should scale the image accordingly at any higher resolution.
- Do not try to change the resolution in-game.

## Heads-up for reversing
The IDA database is provided. Note that the intro video cannot be played during debugging. Disable it in Data/Script/GameParameters.pis (Text File). Also the patched version does not work inside a VM because the Microsoft Basic Display Adapter only supports a maximum resolution of 1280x1050. The display initialisation IDirectDraw7::setDisplayMode() will fail. You have to use a "real" GPU driver. 

## Credits
Thanks to the team at elishacloud for developing the dxwrapper and to my friends for giving me new inspirations when i was stuck reverse engineering. And of course all the credits to the people at Eidos and DeepRed for developing the game in the first place.

  

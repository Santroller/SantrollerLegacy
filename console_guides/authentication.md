# Authentication controllers
Some consoles check if a controller is a genuine controller. Our controllers are unoffical, so we need to trick the console into thinking our controller is genuine.

The legacy AVR firmware cannot pass authentication through another controller. You must instead use a supported unauthenticated input mode or patch authentication out where possible.

1. Patch out authentication, as with [UsbdSecPatch](https://github.com/InvoxiPlayGames/UsbdSecPatch).
2. Use a game-supported input method that does not need authentication, such as PS3 instruments in Rock Band 4 or keyboard input in Fortnite Festival.

## Consoles needing authentication
- Xbox 360
    - The Xbox 360 in most cases requires authentication, but Santroller has authentication keys built in. 
- Xbox One and Series S|X, but only if you are not playing Fortnite Festival. 
    - For Fortnite Festival, you can follow the [Fortnite Festival](https://santroller.tangentmc.net/tool/fortnite_festival.html) guide.
- PS4
    - For Rock Band 4, you can use PS3 mode. Do note however that when you do this, it will only work in game, and not the PS4 system menu.
    - For Rock Band 4 and GHL, you can patch the game to support other instruments using [OrbisInstrumentalizer](https://github.com/InvoxiPlayGames/OrbisInstrumentalizer) if you have a GoldHEN modded PS4.
    - For Fortnite Festival, you can follow the [Fortnite Festival](https://santroller.tangentmc.net/tool/fortnite_festival.html) guide.
- PS5
    - For Fortnite Festival, you can follow the [Fortnite Festival](https://santroller.tangentmc.net/tool/fortnite_festival.html) guide.
    - For Rock Band 4, you can use PS3 mode. Do note however that when you do this, it will only work in game, and not in the PS5 system menu.
    - For any other game, you require the [Besavior P5General](https://p5general.com).

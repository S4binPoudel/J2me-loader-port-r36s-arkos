Extract J2me loader port r36s arkos.zip and put all files inside roms/ports folder.
Supports all 2d/3d j2me games including mascot 3d, m3g .


J2ME Loader for R36S
====================

Plays Java ME (J2ME / MIDP 2.0) phone games on the R36S and other ArkOS
handhelds. It is a port of J2ME Loader (the Android emulator) to Linux:
same MIDP runtime, same vendor APIs, same 3D engines, running on the
PortMaster Java runtime with SDL2 and the device's OpenGL ES GPU.

What works
----------
- MIDP 2.0 / CLDC 1.1: Canvas, GameCanvas, Forms and all lcdui items,
  game API (Sprite, TiledLayer, LayerManager), RecordStore saves, file and
  resource connections, JAD/manifest properties.
- Sound (JSR-135): MIDI, XMF, tone sequences, RTTTL/iMelody/OTA ringtones,
  SMAF/MMF, WAV (incl. IMA ADPCM) and MP3; MIDIControl, ToneControl,
  VolumeControl. Optional DLS soundbank for MIDI.
- 3D, all on the GPU:
    * JSR-184 M3G (Nokia's reference engine)
    * Mascot Capsule v3 (micro3d), and the Vodafone / Motorola / JBlend
      Mascot v1 style APIs built on it
    * JSR-239 OpenGL ES 1.1 (EGL + GL10/GL11 + OES extensions)
    * Nokia M3D and Mexa OPGL
  Devices without GLES 1.1 drivers are handled by a built-in GLES 1.1 on
  GLES 2.0 layer.
- Vendor APIs: Nokia UI (FullCanvas, DirectGraphics, DeviceControl, Sound),
  Siemens, Samsung, Motorola, Sony Ericsson, Vodafone / J-Phone, KDDI,
  Sprint, Mexa and others from J2ME Loader.

Installing games
----------------
Copy .jar files (with their .jad if you have it) into

    ports/j2meloader/games/

Folders roms/j2me and roms2/j2me are scanned too. Start "J2ME Loader"
from the Ports menu and pick a game.

Controls (default)
------------------
    D-pad / left stick   phone arrows (UP DOWN LEFT RIGHT)
    A                    FIRE / OK (centre key)
    B                    5
    X / Y                1 / 3
    L1 / R1              left / right soft key
    L2 / R2              * / #
    right stick          2 / 8 / 4 / 6
    L3 / R3              5 / 0
    START                on-screen phone keypad (all 12 keys)
    SELECT               menu (pause, picture, controls, settings,
                         screenshot, restart, exit)
    SELECT + START       quit

Every button can be remapped per game: menu > Controls. Some phones use
other key codes; if a game ignores the soft keys try menu > Game settings >
Key codes (nokia / siemens / motorola).

Picture
-------
menu > Picture: rotation (90/270 fills the 640x480 screen with a 240x320
game when you hold the device sideways), scaling (fit / integer / stretch),
filter (sharp / nearest / linear) and an FPS limit for games that run too
fast.

Settings and saves
------------------
    config/global.properties     settings for all games (see the
                                 commented global.properties.example)
    config/games/<game>.properties  per game (written by the menus)
    data/<game>/                 saves (RecordStores) and files
    screenshots/                 menu > Save screenshot
    soundbanks/                  DLS soundbanks for MIDI; select one with
                                 sound.soundbank=<file> in a .properties
    log.txt                      log of the last run

Notes
-----
- Games that need a network, Bluetooth, camera, GPS or SMS start, but
  those features report themselves unavailable.
- The first start of a game takes a few seconds while Java warms up.
- If a game shows a black screen, try the other "Key codes" layout or a
  different screen size (Game settings), and check log.txt.

Licenses: see LICENSE (Apache 2.0) and NOTICE (third-party components).

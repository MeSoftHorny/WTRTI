<h1 align="center">WTRTI</h1>

<p align="center">
<a href="https://github.com/MeSoftHorny/WTRTI/releases" alt="Downloads">
        <img src="https://img.shields.io/github/downloads/MeSoftHorny/WTRTI/total?style=for-the-badge&color=228B22" /></a>

<a href="https://github.com/MeSoftHorny/WTRTI/releases/latest" alt="Latest release">
        <img src="https://img.shields.io/github/v/release/MeSoftHorny/WTRTI?style=for-the-badge" /></a>
</p>
<p align="center">
<a href="https://discord.gg/XAEYmRM5NG" alt="Discord">
        <img src="https://img.shields.io/discord/1125375463880138802?logo=discord&label=Discord&style=for-the-badge&color=483D8B" /></a>
<a href="https://www.patreon.com/wtrti" alt="Support">
        <img src="https://img.shields.io/badge/Patreon-Support_-red?style=for-the-badge&logo=patreon" /></a>
          
</p>
<h1 align="center"></h1>

**WarThunder Real-Time Information**, a highly customizable HUD overlay and logging tool for War Thunder.

<h1 align="center"></h1>

### Features:
- More than 30 types of indicators (Climb, AoA, Turning time, Turning radius, Fuel consumption, WEP remain, Booster remain, etc.).
- Two types of OSD (On-screen display):  
      RTSS - using "RivaTuner Statistics Server" OSD functionality. Works with any window mode.  
      WTRTI - Borderless window with transparency. *Requires "Fullscreen Window" mode to be enabled.*
- Custom indicators, allows you to make a new indicators with a specific reading properties from localhost:8111.
- Lua scripts, for custom processing of indicator values.
- Custom "Alert" conditions for indicators, with Sound triggering.
- VR support (SteamVR only).
- Per-vehicle profile, with automatic loading at the beginning of a battle.
- Logging flight data into .csv file (Comma-separated values).
- "Game chat" window, with ability translate in-game chat messages by opening Google Translate web-page or in-app translate (Lingva.ml).
- "Battle Log" window, with a keyword highlight.


<h1 align="center"></h1>

### How it works:
WTRTI does not make any changes to the game process or its data, it 'only' processes data from localhost:8111(web-map) and displays it on a screen.

<h1 align="center"></h1>

### Installation:
1. Download [the latest version](https://github.com/MeSoftHorny/WTRTI/releases)
2. Extract it to a seperate folder with write permissions. Make sure it is not in the game root directory, otherwise the game launcher will delete WTRTI.exe file in there.
3. Run WTRTI.exe.


### Upgrade from previous versions:
Simply extract the downloaded zip file into the folder where the old version is located.


<h1 align="center"></h1>

### System requirements:

- Game: Full client+  
*DEV Server or Minimal client users, see Troubleshooting section for a workaround.*
- OS: Windows: 7 or higher  
Linux: Ubuntu 20.04 and later  
*Borderless window mode requires Compositor to be enabled.*  
- Graphics: Any OpenGL 3.3 compatible GPU or greater  
*RTSS OSD: Rivatuner Statistics Server v7.3+. [Download](https://www.guru3d.com/files-details/rtss-rivatuner-statistics-server-download.html)*
- VR: SteamVR

<h1 align="center"></h1>

### Troubleshooting:
_**"Not working with DEV server":**_  
    WTRTI may not work, if the vehicle does not have a cockpit or the game client is Minimal, which causes the indicators.json file to be missing on localhost:8111.  
    In this case, try enabling "Handle data in every game mode" (Settings -> Advanced tab).  
    Beware: Some of the indicators will not work (e.g Critical AoA, Wing Flutter), due to the limited amount of data available from localhost:8111.  

_**"OSD is not show up" or "Data is not updated in the main window":**_  
    If you have Antivirus, try to add exclusion for WTRTI.  
 
_**"The overlay is stuttering/freezing" or "Data is not updating when ALT-TAB to the game":**_  
    Try to turn off the "Hardware Accelerated GPU Scheduling": https://www.thenerdmag.com/how-to-turn-off-hardware-accelerated-gpu-scheduling-on-windows-10/  

_**"RTSS OSD is not working":**_  
    RTSS may conflict with other overlays, try disabling them first.  
    If you running the game through Steam, you can disable overlay for War Thunder, just open Properties->General-> Uncheck the "Enable the Steam Overlay while in-game"  
 

_**"WTRTI OSD: transparency is not working/black rectangle":**_  
    Windows: The Compositor on your system is not working properly. Can be a few things:  
        1. Graphics driver issue, try to reinstall.  
        2. Windows is corrupted (sfc /scannow).  
    Linux: Try to enable the compositor (kwin, compiz, picom).  
 
_**"Flight data is not being written to the CSV file":**_  
    Perhaps Antivirus restricts write access, try to add exclusion for WTRTI.  

<h1 align="center"></h1>

**[More Info (Archived Forum)](https://old-forum.warthunder.com/index.php?/topic/483838-warthunder-real-time-information)**

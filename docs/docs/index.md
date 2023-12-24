# Welcome to WTRTI

A highly customizable HUD overlay and logging tool for War Thunder.  

![#](images/wtrti_themes.png)


[Download](https://github.com/MeSoftHorny/WTRTI/releases/latest/){ .md-button .md-button--primary }
[WIP Versions](https://patreon.com/wtrti){ .md-button .md-button--primary }

## Features
- More than 30 types of indicators (Climb, AoA, Turning time, Turning radius, Fuel consumption, WEP remain, Booster remain, etc.).  
!!! info
    Ammo related information is not available (or very limited) in the web-map, so it cannot be added to the app.
- Two types of OSD (On-screen display):  
    - **WTRTI** - Built-in OSD. Borderless window with transparency, that requires "Fullscreen Window" mode to be enabled. See [OSD Setup](features.md#wtrti-built-in).  
    - **RTSS** - using "RivaTuner Statistics Server" OSD functionality. Works with any window mode.  
- VR support (**SteamVR only**).
- **Custom indicators**, allows you to make a new indicators with a specific reading properties from localhost:8111.
- **Lua** scripts, for custom processing of indicator values.
- Custom "Alert" conditions for indicators, with Sound playback.
- Per-vehicle profile, with automatic loading at the beginning of a battle.
- Hotkey actions (e.g. Profile loading).
- Logging the flight data to CSV file.
- "Game chat" window, with ability translate in-game chat messages by opening Google Translate web-page or 'in-app' translate ([Lingva.ml](https://lingva.ml)).
- "Battle Log" window, a keyword highlight of the battle events.
- Experimental **DCS World** support, see [DCS World Setup](features.md#dcs-world-setup).

## How it works
This is **not** a mod.  
WTRTI **does not** make any changes to the game process or its data, it 'only' processes data from **localhost:8111**(web-map) and displays it on a screen (Overlay).

## Installation
1. Download [**the latest version**](https://github.com/MeSoftHorny/WTRTI/releases/latest).
2. Extract it to a seperate folder with **write permissions**.
>**Note**: Make sure it is not in the game root directory, otherwise the game launcher will delete WTRTI.exe file in there.
3. Run WTRTI.exe.
4. Add some indicators (**+** button) to the list.
5. [Setup the game for OSD](features.md#wtrti-built-in)

### Upgrade from previous versions
Simply extract the downloaded zip file into the folder where the old version is located.

## System requirements
- **Game**: Full client+  
> **Note:** **DEV Server** or **Minimal client** users, see [Troubleshooting](troubleshooting.md#not-working-with-dev-server) for a workaround.
- **OS**: **Windows** 7 or higher.  
**Linux**: Ubuntu 20.04 and later. X11.  
*Borderless window mode requires Compositor (eg. kwin, compiz).*  
*Since v2.2.5, you can use __Gamescope (v3.11.0+)__, See [How-To](features.md/#gamescope-setup-linux).*  
- **Graphics**: Buit-in OSD: Any OpenGL 3.3 compatible GPU or greater.  
*RTSS OSD: Rivatuner Statistics Server v7.3+. [Download](https://www.guru3d.com/files-details/rtss-rivatuner-statistics-server-download.html)*
- **VR**: SteamVR. See [VR](features.md/#vr) for more info.

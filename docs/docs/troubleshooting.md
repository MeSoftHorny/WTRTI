## The overlay is stuttering/freezing or Data is not updating when ALT-TAB to the game
Try to turn off the "Hardware Accelerated GPU Scheduling" (HAGS).  
**How-To:** <https://obsproject.com/kb/hags>

## Not working with DEV server
WTRTI may not work if a vehicle does **not** have a cockpit or the game client is **Minimal**, causing some information(**indicators.json**) to be missing on localhost:8111.  
In this case, you can try enabling **"Handle data in every game mode"** (**Settings -> Advanced tab**).  
!!! info
    Some indicators may not work due to the limited amount of data available from the localhost:8111, e.g. Critical AoA, Critical Air Speed.
!!! warning
    At some point, the overlay may continue to be displayed when you are in the menu, in which case try disabling this option.

## OSD is not show up" or "Data is not updated in the main window
If you have antivirus, try adding an exclusion for WTRTI.

## RTSS OSD is not working
RTSS may conflict with other overlays, try disabling them first.  
If you running the game through Steam, try to disable Steam Overlay for War Thunder, just open Properties->General-> Uncheck the "Enable the Steam Overlay while in-game".

## WTRTI OSD: transparency is not working/black rectangle
First try to restart your PC.  
**Windows:** The Compositor on your system is not working properly.  
Can be a few things:  
- Graphics driver issue, try to reinstall.  
- Windows is corrupted (sfc /scannow).  
**Linux:** Ensure that the compositor is enabled (kwin, compiz, picom).

## Flight data is not being written to the CSV file
Perhaps Antivirus restricts write access, try to add exclusion for WTRTI.

## Fuel consumption indicators not working
The "fuel" value in the localhost:8111 (web-map) is missing on some aircraft (e.g. some early Yak's).  

_Before bug-report to me, check for the "**fuel**" in the "State" window (press F2 in the main window), while you in "Test Flight"._

## Radar Altitude does not work
The "**radio_altitude**" value in the localhost:8111 may be missing on some aircraft, because the aircraft does not have a radar altitude or the value is displayed on a digital device (modern jets).  


## The overlay is stuttering/freezing or Data is not updating when ALT-TAB to the game
Try to turn off the "Hardware Accelerated GPU Scheduling":  
<https://www.thenerdmag.com/how-to-turn-off-hardware-accelerated-gpu-scheduling-on-windows-10/>

## Not working with DEV server
WTRTI may not work, if the vehicle does not have a cockpit or the game client is Minimal, which causes the indicators.json file to be missing on localhost:8111.  
In this case, try enabling "Handle data in every game mode" (Settings -> Advanced tab).  
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
**Windows:** The Compositor on your system is not working properly.  
Can be a few things:  
- Graphics driver issue, try to reinstall.  
- Windows is corrupted (sfc /scannow).  
**Linux:** Ensure that the compositor is enabled (kwin, compiz, picom).

## Flight data is not being written to the CSV file
Perhaps Antivirus restricts write access, try to add exclusion for WTRTI.

## Fuel consumption indicators not working 
The "fuel" value in localhost:8111 (web-map) is missing on some aircraft (e.g. some early Yak's).  
Before **bug-report**, check for the "fuel" in "State"" window (press F2 in the main window), while you in Test Flight.


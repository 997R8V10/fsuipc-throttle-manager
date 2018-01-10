# Throttle Manager 2.0.0
- **By:** pilotjohn@gearsdown.com
- **Modified By:** prithvisagar.shivaraman@gmail.com
- **Sounds:** http://www.freesound.org/people/milton./packs/5284/

## Description
This Throttle Manager provides the functionality to have both forward and reverse thrust on single axes by allowing the user to toggle between modes through joystick buttons. It can be configured to auto-toggle to forward thrust, configured for various amount of throttle levers, and works for almost every aircraft in Flight Simulator.
A huge thanks to PilotJohn who originally created Throttle Manager 1.2.0. You can find the original here: https://github.com/IslandJohn/SimTools/tree/master/Miscellaneous

## Pre-requisites
This requires a registered copy of FSUIPC. Any version for FSX or P3D including v4 will work.

## Installation and Setup
1. Depending on how many throttle levers you have, copy the appropriate `ThrottleManager.lua.*lev` file into the `Modules` folder.
	1. If you wish to have throttle toggle sounds, copy all the `.wav` files into the `Modules` folder.
2. Edit the `FSUIPC*.ini` and add the following (where `X` is the next number in the sequence, or `1` if it's the first entry):
	```
    [Auto]
    X=Lua ThrottleManager
    ```
### Throttle Setup with FSUIPC
1. Open the Simulator.
2. Go to `Settings->Controls` and delete all joystick assignments for all throttle assignments (even if you have less than 4 levers).
3. Go to `Add-ons->FSUIPC`.
4. Repeat the following steps for each throttle lever on your joystick:
	1. Go to the `Axis Assignment` tab.
	2. Move the lever.
	2. Select `Send direct to FSUIPC Calibration`
	3. Check `Throttle N` where N is the lever number starting from 1.
	4. Go to the `Joystick Calibration` tab.
	5. On page `3 of 11: Separate throttles per engine`, check `No reverse Zone` and Set `Min` and `Max` for throttle N, where N is the lever number.
	6. **DO NOT** configure more throttles than you have, or check any of the `1->...` check boxes.

### Toggle Button Setup 
Depending on the amount of levers you have, you may want to have 1, 2, or even 4 toggle buttons. However many you choose, you must note that all 4 simulator throttles must be toggled for this to work correctly. To get around the issue of having less toggle buttons than the amount of throttles, we will assign each button(s) to multiple reversers.
1.  Go to the `Buttons + Switches` tab.
2.  For each toggle button:
	1. Press the button you want for reverser toggle.
	2. Check `Select for FS control`
	3. Choose `LuaToggle ThrottleManager`
	4. Enter `N` for the `Parameter` where `N` is the number of the first reverser the button will toggle. For example, if you had 2 toggle buttons, the first toggle button would map to both 1 and 2, but we would input 1 initially, and the second toggle button would map to both 3 and 4, but we would input 3 initially.
	5. Open `FSUIPC*.ini` and go to the `[Buttons]` section.
	6. Find the lines with `-{LuaToggle ThrottleManger}-` and copy and paste them to cover all 4 reversers. \
	 An example is as follows for one toggle button:
    ```
    6=P0,11,CL3:T,1 	-{LuaToggle ThrottleManager}-
	7=P0,11,CL3:T,2 	-{LuaToggle ThrottleManager}-
	8=P0,11,CL3:T,3 	-{LuaToggle ThrottleManager}-
	9=P0,11,CL3:T,4 	-{LuaToggle ThrottleManager}-
    ```
    7. Back in the FSUIPC config window, hit reload buttons.

## Configuration
Further configuration can be achieved by editing the `throttles` array.
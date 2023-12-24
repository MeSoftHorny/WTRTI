## General
Template Script looks like this:
```
----
-- arguments: in_value:   "State Key" value
--            value_idx:  multi-value index
---
-- return: first(number):   final value
--         second(boolean): value is updated or not
--
function value_proc(in_value, value_idx)
   local value = in_value

   return value, true
end
```

The `value_proc` function will be called for every available value index (up to 8).  

!!! warning
    If the script fails, it will be silently kicked, and the value will be `N/A`.  
    Check the `Logs/WTRTI.log` file for error messages.

## Functions

#### getStateValue(state_key_str)
Returns the state value, otherwise a `nil` if the key not found.  
> **Note:** Press **F2** in the main window to display the State window.

__Usage:__  
`local rpm = getStateValue("RPM 1")`

#### getVehicleData(veh_key_str)
Returns values from FM database.  
__Usage:__  
`local crit_spd = getVehicleData("crit_spd")`

<!-- Lets make it a bit looooong -->
| Key&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Description |
| :--- | --- |
| `type`  | string, returns Vehicle's Type (fighter, bomber, helipoter, etc). |
| `name` | string, returns Vehicle's Name (yak3, bf-109_g6, etc). |
| `empty_mass` | number, returns Empty Mass, kg. |
| `max_fuel_mass` | number, returns Mass with max Fuel, kg. |
| `crit_spd` | number, returns Critical Air Speed, km/h. |  On Vehicles with Variable WingSpan, returns speed at minimum wing sweep. |
| `crit_max_spd` | number, returns Critical Air Speed at maximum Wing Sweep on Vehicles with Variable WingSpan. |
| `crit_mach_spd` | number, returns Critical Air Mach Speed. |
| `crit_max_mach_spd` | number, returns Critical Air Mach Speed on Vehicles with Variable WingSpan at maximum wing sweep. |
| `crit_combat_flaps_spd` | number, returns Critical Combat Flaps Speed, km/h. |
| `crit_takeoff_flaps_spd` | number, returns Critical Takeoff Flaps Speed, km/h. |
| `crit_landing_flaps_spd` | number, returns Critical Landing Flaps Speed, km/h. |
| `crit_flaps_spd` | array of numbers, returns Critical Flaps Speed, km/h.<br> `[ pos1, spd1, pos2, spd2, ... ]` |
| `crit_gear_spd` | number, returns Critical Gear Speed, km/h. |
| `combat_flaps_pos` | number [0, 1], Combat flaps position. |
| `takeoff_flaps_pos` | number [0, 1], Takeoff flaps position. |
| `num_engines` | number, Number of Engines. |
| `max_nitro` | number, amount of Nitro, kg. |
| `nitro_consume` | number, Nitro consumption, kg/s. |
| `vne` | array of numbers, returns Critical Air Speed, km/h.<br> `[ pos, spd ]` <br> When Variable WingSpan:<br> `[ pos1, spd1, pos2, spd2, ... ]` |
| `vne_mach` | array of numbers, returns Critical Air Speed, km/h.<br> `[ pos, spd ]` <br> When Variable WingSpan:<br> `[ pos1, spd1, pos2, spd2, ... ]` |
| `crit_aoa` | array of numbers, returns Critical AoA.<br> `[ aoa_positive1, aoa_negative1, aoa_positive2, aoa_negative2, ... ]` <br> When Variable WingSpan:<br> `[ wing_pos1, aoa_positive1, aoa_negative1,`<br> `wing_pos2, aoa_positive2, aoa_negative2, ... ]` |
| `crit_wing_overload` | array of numbers, returns Critical Wing Overload (N).<br> `[ positive_overload, negative_overload ]` <br> When Variable WingSpan:<br> `[ wing_pos1, positive_overload1, negative_overload1,` <br> `wing_pos2, positive_overload2, negative_overload2, ... ]` |
| `rpm_range` | array of numbers, returns RPM range.<br> `[ min_rpm, max_rpm, crit_rpm ]` |

#### getUpdateTime()
Returns the current update time in seconds.

#### getTime()
Returns the current time in seconds from the start of the application.


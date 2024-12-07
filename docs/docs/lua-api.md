## General
Template Script looks like this:
```
---
-- return: none
--
function init_proc()

end

---
-- arguments: in_value:   "State Key" value
--            value_idx:  multi-value index (0 - based)
---
-- return: first(number):   final value
--         second(boolean): value is valid or not
---
function value_proc(in_value, value_idx)
   local value = in_value

   return value, true
end

---
-- arguments: in_value:   number
--            value_idx:  multi-value index (0 - based)
---
-- return: string
---
-- function value_str_proc(in_value, value_idx)
--   local str = string.format("%.2f", in_value)
--
--   return str
-- end
```

The pipeline looks like this:  
**"State value"** -> **value_proc** -> **value_str_proc**

The script file runs in a **sandboxed environment**, that includes a few standard libs:  
```
math
string
table
```

With some functions from the `base` library:  
```
assert
error
ipairs
pairs
next
select
tonumber
tostring
type
pcall
xpcall
``` 

Each script can contain the following callback functions:  

| Key&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Description |
| :--- | --- |
|`init_proc()` | called once at a new Vehicle or when Script Options has been changed.|
|`value_proc(state_value, value_idx)` | called at every update, for each available value index (up to 8).|
|`value_str_proc(value, precision)` | called at every update, number -> string.|

!!! warning
    If the script fails, it will be silently kicked, and the value will be `N/A`.  
    Check the `Logs/WTRTI.log` file for error messages.


## Functions

#### getStateValue(state_key_str [, default_value])
Returns the state value, otherwise a `nil` if the key not found.  
or  
Returns `default_value` if specified.  
> **Note:** Press **F2** in the main window to display the "State" window.

__Usage:__  

```
local rpm = getStateValue("RPM 1")
if rpm then
    -- code
end
```
**or**

`local rpm = getStateValue("RPM 1", 0)`


#### setStateValue(state_key_str, value)
Allows you to emplace the value into the "State" list.  

Returns `true` if the state value has been emplaced, `false` if not.  

> **Note:** Only non-existent keys are allowed to be emplaced.  
> **Note:** The key lifetime is only one frame (update).  

__Usage:__  
`setStateValue("new_key", 3.14)`

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
| `crit_gear_spd` | number, returns Critical Landing Gear Speed, km/h. |
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


## Script Options
Allows you to specify additional options for the custom indicator that will be displayed on the Script tab (GUI).  
In the script, declare a global table `__OPTIONS`, example:  

```
__OPTIONS = {
   {
      key  = "option_key", -- key to get/set value in the script
      name = "Sample Option", -- name in GUI
      type = "boolean", -- type of the option
      value = true -- default value
   },
   {
      key  = "combo_option__key",
      name = "Sample Combo",
      type = "combo",
      options = { "red", "blue", "green" }
      value = 2, -- default selected option (green)
   },
}
```

**Note:** When you set the options in GUI and click on the OK/Apply button the `init_proc` function will be called.  
**Note:** On the script "Hot-Reload" (F9), these options will be reseted to defaults.  


### Types
|  Type | Value |
| :--- | --- |
| boolean | true, false |
| integer | any natural number |
| float | real number |
| string | string |
| radio | integer, index of the `options`, begins from 0 |
| combo | integer, index of the `options`, begins from 0 |
| hotkey | none |

### Functions
#### getOptionValue(key_str [, default_value])
Returns the option value.  
__Usage:__  
`local opt1 = getOptionValue("option_key")`  

or with default value:  

`local opt1 = getOptionValue("option_key", "Default String")`  

#### setOptionValue(key_str, value)
Allows to set a value for the option.  
__Usage:__  
`setOptionValue("option_key", "New String")`  

**Note:** Only initial type of the value is allowed to set.  

### Groups
You can make a group of the options, simply add a name key to the table right before the options.  

```
__OPTIONS = {
   name = "Group1"
   {
      key  = "option_key",
      name = "Sample Option",
      type = "boolean",
      value = true
   },
   {
      name = "Group2" -- group inside of the Group1
      {
         key  = "option_key_2",
         name = "Sample Option 2",
         type = "boolean",
         value = true
      },
      {
         key  = "option_key_3",
         name = "Sample Option 3",
         type = "boolean",
         value = false
      }
   }
}
```
Maximum level of group depth is 2.  

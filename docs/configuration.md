---
myst:
  enable_extensions: ["colon_fence"]
---

# Configuration

The card can be configured through the following attributes:

| Attribute | Requirement | Default |Description |
| --- | --- | --- | --- |
|type: | **Required** | `custom:sunsynk-power-flow-card`| The custom card |
|cardstyle: | **Required** | `lite` | Selects the card layout that is used  `lite` or `full` |
|panel_mode:| Optional | `false` |Toggles panel mode removing any card height restrictions. For use with Panel(1 card) view types or grid layouts|
|large_font:| Optional | `false` | Increases font size of sensor data |
|title:| Optional | `` | Set the card title i.e. Inverter One |
|title_colour:| Optional | `` | Changes the colour of the card title. (`red`, `green`, `blue` etc) |
|title_size:| Optional | `32px` | Set the font size for the card title i.e. `16px`, `24px` |
|show_solar:| Optional |`true` | Toggle display of solar information |
|show_battery:| Optional |`true` | Toggle display of battery information |
|card_height:| Optional | `396px` | Sets the card height in pixels `400px` |
|decimal_places:| Optional | `2` | Sets the number of decimal places to display when using the `auto_scale` option. |
|inverter: | Optional | See optional [Inverter](#inverter) attributes below  |List of inverter attributes.  |
|battery: | Optional  | See required [Battery](#battery) attributes below | List of battery attributes. Required if `show_battery: true`  |
|solar: | Optional |See optional [Solar](#solar) attributes below | List of solar attributes.  |
|load: | Optional | See optional [Load](#load) attributes below|List of load attributes.  |
|grid: | Optional | See optional [Grid](#grid) attributes below| List of grid attributes.  |
|entities:|**Required** |See required [Entities](#entities) attributes below | List of sensor entities. |

### Inverter

| Attribute | Requirement |Default | Description |
| --- | --- | --- |--- |
|modern:| Optional |`true`| Changes the inverter image.|
|colour:| Optional |`grey`| Changes the colour of the inverter. Hex codes (`'#66ff00'` etc) or names (`red`, `green`, `blue` etc) |
|autarky:| Optional| `power`| Display autarky and ratio as a percentage using either realtime power or daily energy values. Set to `no` to hide (`energy/power/no`). <br />Autarky is the percentage of self sufficiency through Home Production. Ratio is the percentage of produced electricity used by the home. <br />It is calculated based on the formula below and borrowed from the [Power Distribution Card](https://github.com/JonahKr/power-distribution-card)  <br /><ul><li>Autarky in Percent = Home Production / Home Consumption </li><li>Ratio in Percent = Home Consumption / Home Production</li></ul>|
| model: | Optional | `sunsynk` | Selects which status codes to use. Set to `lux` for Lux inverters. Set to `goodwe` for Goodwe inverters.  |
|auto_scale: | Optional | `false` | If set to `true` power values greater than 999W will be displayed as kW e.g. 1.23kW. The number of decimal places can be changed using the `decimal_places` card attribute|
| three_phase: | Optional | `false` | If set to `true` additional 3 phase sensors will be displayed. Requires entity attributes to be defined i.e. `inverter_current_L2`, `inverter_current_L3`, `inverter_voltage_L2`, `inverter_voltage_L3` , `grid_ct_power_L2`, `grid_ct_power_L3`, `load_power_L1`, `load_power_L2`, `load_power_L3`
### Battery

To display battery power and current as absolute values set `show_absolute: true`. This is set to false by default and will return your sensor value. The animated dot will change direction depending on the charging or discharging state. The `invert_power` attribute can be used to reverse direction if needed by your sensor.

| Attribute | Requirement |Default | Description |
| --- | --- | --- |--- |
|energy: | **Required** | `0` | Total battery energy in Wh (e.g. 3 x 5.32kWh = 15960). If set to `0` the remaining battery runtime will be hidden|
|shutdown_soc: | **Required** | `20` |The battery shutdown percentage used to calculate remaining runtime. Numeric value or sensor i.e. `sensor.sunsynk_battery_capacity_shutdown`  |
|invert_power:| Optional | `false`|Set to `true` if your sensor provides a positive number for battery charge and negative number for battery discharge|
|colour:| Optional| `pink`| Changes the colour of all the battery card objects. Hex codes (`'#66ff00'` etc) or names (`red`, `green`, `blue` etc) |
|show_daily: | Optional| `false` | Toggles the daily total |
|animation_speed: | Optional | `6` | Set slowest animation speed in seconds, depending on power draw |
|max_power: | Optional | `4500` | Maximum power draw to calculate animation speed |
|full_capacity: | Optional| `80` | If SOC >= to this value the fully charged battery image will be shown. Accepts any value between 80-100|
|empty_capacity: | Optional | `30` | If SOC <= to this value the empty battery image will be shown. Accepts any value between 1-30
|show_absolute: | Optional | `false` | set to `true` to display power and current as absolute values
|auto_scale: | Optional | `false` | If set to `true` power values greater than 999W will be displayed as kW e.g. 1.23kW. The number of decimal places can be changed using the `decimal_places` card attribute|

### Solar

These attributes are only needed if `show_solar` is set to `true`
| Attribute | Requirement |Default | Description |
| --- | --- | --- |--- |
|colour:| Optional | `orange` | Changes the colour of all the solar card objects. Hex codes (`'#66ff00'` etc) or names (`red`, `green`, `blue` etc) |
|show_daily: | Optional | `false` | Toggles the daily total |
|display_mode: | Optional | `1` | `1` - Only display the daily total, `2` - Display the daily total and remaining daily forecast, `3` - Display the daily total and total solar generation |
|mppts: | **Required** | `2` | Specify the number of MPPT's in use `1`, `2`, `3` or `4` |
|animation_speed: | Optional | `9` | Set slowest animation speed in seconds, depending on Power produced |
|max_power: | Optional | `8000` | Maximum power draw to calculate animation speed |
|pv1_name: | Optional | `PV1` | Set the disaply name for MPPT1 |
|pv2_name: | Optional | `PV2` | Set the disaply name for MPPT2 |
|pv3_name: | Optional | `PV3` | Set the disaply name for MPPT3 |
|pv4_name: | Optional | `PV4` | Set the disaply name for MPPT4 |
|auto_scale: | Optional | `false` | If set to `true` power values greater than 999W will be displayed as kW e.g. 1.23kW. The number of decimal places can be changed using the `decimal_places` card attribute|

### Load

| Attribute | Requirement | Default | Description |
| --- | --- | --- |--- |
|colour:| Optional |`'#5fb6ad'`| Changes the colour of all the load card objects. Hex codes (`'#66ff00'` etc) or names (`red`, `green`, `blue` etc) |
|show_daily: | Optional |`false` | Toggles the daily total. |
|show_daily_aux" | Optional |`false` | Toggles the daily AUX total. Only displayed if `show_aux` is set to `true` |
|show_aux: | Optional | `false` | Toggles the display of AUX |
|invert_aux: | Optional | `false` | Set to `true` if your sensor provides a positive number for AUX input and negative number for AUX output  |
|show_absolute_aux: | Optional | `false` | set to `true` to display power as an absolute value
|animation_speed: | Optional | `8` | Set slowest animation speed in seconds, depending on Power draw |
|max_power: | Optional | `8000` | Maximum power draw to calculate animation speed |
|aux_name: | Optional | `Auxilary` | Set the display name for the AUX Load
|aux_type: | Optional | `default` | Changes the AUX image using preset or any mdi icon e.g. `mdi:ev-station`. Presets are: `gen`, `inverter` `default`, `oven`, `pump`, `aircon` and `boiler`.
|aux_colour:| Optional | `the load colour` | Changes the colour of all the AUX card objects. Hex codes (`'#66ff00'` etc) or names (`red`, `green`, `blue` etc) |
|aux_off_colour:| Optional| `the load colour` | Changes the colour of the AUX icon and label when disconnected. Hex codes (`'#66ff00'` etc) or names (`red`, `green`, `blue` etc) |
|aux_loads:| Optional | `0` | Display additional loads on the AUX side (`0/1/2`)
|aux_load1_name: |Optional | | Set the display name for the AUX load 1
|aux_load2_name: |Optional | | Set the display name for the AUX load 2
|aux_load1_icon: | Optional | | Change the AUX load 1 image using any mdi icon e.g. `mdi:ev-station`
|aux_load2_icon: | Optional | | Change the AUX load 2 image using any mdi icon e.g. `mdi:ev-station`
|additional_loads: | Optional | `0` | Display additional loads on the essential side (`0/1/2/4`)
|load1_name: | Optional |  | Set the display name for the essential load 1
|load2_name: | Optional |  | Set the display name for the essential load 2
|load3_name: | Optional |  | Set the display name for the essential load 3 (Lite card only)
|load4_name: | Optional |  | Set the display name for the essential load 4 (Lite card only)
|load1_icon: | Optional | none | Change the essential load 1 image using preset or any mdi icon e.g. `mdi:ev-station` Presets are: `boiler`, `pump`, `aircon`, `oven` |
|load2_icon: | Optional | none | Change the essential load 2 image using preset or any mdi icon e.g. `mdi:ev-station` Presets are: `boiler`, `pump`, `aircon`, `oven` |
|load3_icon: | Optional | none | Change the essential load 3 image using any mdi icon e.g. `mdi:ev-station` Presets are not available when showing 4 essential loads |
|load4_icon: | Optional | none | Change the essential load 4 image using any mdi icon e.g. `mdi:ev-station` Presets are not available when showing 4 essential loads |
|auto_scale: | Optional | `false` | If set to `true` power values greater than 999W will be displayed as kW e.g. 1.23kW. The number of decimal places can be changed using the `decimal_places` card attribute|

### Grid

| Attribute | Requirement | Default | Description |
| --- | --- | --- | --- |
|colour:| Optional | `'#5490c2'`| Changes the colour of all the grid card objects. Hex codes (`'#66ff00'` etc) or names (`red`, `green`, `blue` etc) |
|export_colour:| Optional |  | Changes the colour of all the grid card objects when exporting (selling) energy. Hex codes (`'#66ff00'` etc) or names (`red`, `green`, `blue` etc) |
|no_grid_colour:| Optional | `'#a40013'`|Changes the colour of the grid disconnected icon. Hex codes (`'#66ff00'` etc) or names (`red`, `green`, `blue` etc)|
|show_daily_buy: | Optional | `false` | Toggles the daily buy total |
|show_daily_sell: | Optional | `false` | Toggles the daily sell total |
|show_nonessential: | Optional |`false` | Toggles the display of non-essential |
|nonessential_icon: | Optional | `default` | Change the non-essential image using presets or any mdi icon e.g. `mdi:ev-station`. Presets are: <br /> <img height="25px" src="https://api.iconify.design/mdi/house-import-outline.svg"> `default`  <img height="25px" src="https://api.iconify.design/fluent/oven-32-regular.svg"> `oven`, <img height="25px" src="https://api.iconify.design/material-symbols/water-heater.svg"> `boiler` </br> <br/> <img height="25px" src="https://api.iconify.design/material-symbols/water-pump-outline.svg"> `pump`,  <img height="25px" src="https://api.iconify.design/mdi/air-conditioner.svg"> `aircon` </br> |
|nonessential_name: | Optional | `Non Essential` |Set the display name for the non-essential load
|additional_loads: | Optional |`0`| Toggle the display of additional loads on the non-essential side (`0/1/2`)
|load1_name: | Optional |  | Set the display name for the non-essential load 1
|load2_name: | Optional |  |Set the display name for the non-essential load 2
|load1_icon: | Optional | `default` | Change the non-essential load 1 image using presets or any mdi icon e.g. `mdi:ev-station`. Presets are: `default`, `oven`, `boiler`, `pump`, `aircon` |
|load2_icon: | Optional | `default` | Change the non-essential load 2 image using presets or any mdi icon e.g. `mdi:ev-station`. Presets are: `default`, `oven`, `boiler`, `pump`, `aircon` |
|invert_grid:| Optional | `false`| Set to `true` if your sensor provides a negative number for grid import and positive number for grid export |
|animation_speed: | Optional | `8` | Set slowest animation speed in seconds, depending on power draw |
|max_power: | Optional | `8000` | Maximum power draw to calculate animation speed |
|auto_scale: | Optional | `false` | If set to `true` power values greater than 999W will be displayed as kW e.g. 1.23kW. The number of decimal places can be changed using the `decimal_places` card attribute|
|energy_cost_decimals: | Optional | `2` | Sets the number of decimal places to display the buy and sell energy costs 

### Entities

Entity attributes below have been appended with the modbus register # e.g. `pv2_power_187` to indicate which Sunsynk register should be read when configuring your sensors. Replace the default sensors with your own specific sensor names. It is important that your sensors read the expected modbus register value. If you have missing sensors for any attribute set it to none i.e. `day_pv_energy_108: none`. This will hide the sensor data from the card. To display a placeholder with a default value of 0 set it to `zero` or any other value i.e. `solarday_108: zero`.

See the [WIKI](https://github.com/slipx06/sunsynk-power-flow-card/wiki/Sensor-Mappings) for more information on sensor mappings if using other integration methods.

| Attribute |  Requirement | Default | Description |
| --- | --- | --- | --- |
|use_timer_248: | Optional | `switch.sunsynk_toggle_system_timer` | Displays "Use timer" status as an icon next to the inverter. Set to `no` to hide |
|priority_load_243: | Optional |`switch.sunsynk_toggle_priority_load` | Shows if energy pattern is set to priority load or priority battery as an icon next to the inverter. Set to `no` to hide|
|day_battery_discharge_71: | Optional |`sensor.sunsynk_day_battery_discharge` | Daily battery usage (kWh) |
|day_battery_charge_70: | Optional |`sensor.sunsynk_day_battery_charge` | Daily battery charge (kWh) |
|day_load_energy_84: | Optional | `sensor.sunsynk_day_load_energy` | Daily load (kWh) |
|day_grid_import_76: | Optional | `sensor.sunsynk_day_grid_import` | Daily grid import (kWh) |
|day_grid_export_77: | Optional | `sensor.sunsynk_day_grid_export` | Daily grid export (kWh) |
|day_pv_energy_108: | Optional | `sensor.sunsynk_day_pv_energy` | Daily solar usage (kWh) |
|day_aux_energy: | Optional | | Sensor that provides the daily AUX energy (kWh)
|inverter_voltage_154: | Optional | `sensor.sunsynk_inverter_voltage` | Inverter L1 voltage (V) |
|inverter_voltage_L2: | Optional |  | Inverter L2 voltage (V) |
|inverter_voltage_L3: | Optional |  | Inverter L3 voltage (V) |
|load_frequency_192: | Optional | `sensor.sunsynk_load_frequency` | Load frequency (Hz) |
|inverter_current_164: | Optional | `sensor.sunsynk_inverter_current` | Inverter L1 current (A) |
|inverter_current_L2: | Optional |  | Inverter L2 current (A) |
|inverter_current_L3: | Optional |  | Inverter L3 current (A) |
|inverter_power_175: | Optional | `sensor.sunsynk_inverter_power` | Inverter power (W). Required if the essential_power attribute is set to `none` |
|grid_power_169: | Optional | `sensor.sunsynk_grid_power` | Grid power (W) See NOTE below. Use **167** (Grid LD Power) if non-essential and essential readings are wrong. Required if the nonessential_power attribute is set to `none` |
|pv1_power_186: | Optional | `sensor.sunsynk_pv1_power` | PV string 1 power (W)|
|pv2_power_187: | Optional | `sensor.sunsynk_pv2_power` | PV string 2 power (W)  |
|pv3_power_188: | Optional | `sensor.sunsynk_pv3_power` | PV string 3 power (W)  |
|pv4_power_189: | Optional | `sensor.sunsynk_pv4_power` | PV string 4 power (W)  |
|pv_total:| Optional | `none` | Provide a sensor for total pv power. If omitted the card uses internal logic to calculate this based on the pv1-4 power (W)
|battery_voltage_183: | Optional | `sensor.sunsynk_battery_voltage` | Battery voltage (V) |
|battery_soc_184: | **Required** | `sensor.sunsynk_battery_soc` | Battery state of charge (%) |
|battery_power_190: | **Required** | `sensor.sunsynk_battery_power` | Battery power (W). Requires a negative number for battery charging and a positive number for battery discharging. Set the `invert_power:` battery attribute to `yes` if your sensor reports this the other way around |
|battery_current_191: | **Required** |`sensor.sunsynk_battery_current` | Battery current (A) |
|essential_power: | Optional | `none` | The card will automatically calculate this sensor based on the formula below if the attribute is set to `none`. You can overide this by supplying a sensor that measures essential power e.g. `Load power Essential` in the case of Solar Assistant. You should supply a sensor if using `three_phase: true` (W) |
|essential_load1: | Optional | | Sensor that contains the power of your essential load 1 (W)|
|essential_load2: | Optional | | Sensor that contains the power of your essential load 2 (W)|
|essential_load3: | Optional | | Sensor that contains the power of your essential load 3 (W)|
|essential_load4: | Optional | | Sensor that contains the power of your essential load 4 (W)|
|essential_load1_extra: | Optional | | Sensor that contains additional information you want displayed for your essential load 1 e.g. Daily kWh, Temperature etc|
|essential_load2_extra: | Optional | | Sensor that contains additional information you want displayed for your essential load 2 e.g. Daily kWh, Temperature etc
|load_power_L1: | Optional | | Load L1 Power (W)
|load_power_L2: | Optional | | Load L2 Power (W)
|load_power_L3: | Optional | | Load L3 Power (W)
|nonessential_power| Optional | `none`| The card will automatically calculate this sensor based on the formula below if the attribute is set to `none`. You can overide this by supplying a sensor that measures non-essential power e.g.  `Load power Non-Essential` in the case of Solar Assistant.  (W)
|non_essential_load1: | Optional | |Sensor that contains the power of your non-essential load 1 (W)|
|non_essential_load2: | Optional | |Sensor that contains the power of your non-essential load 2 (W)
|grid_ct_power_172: | **Required** | `sensor.sunsynk_grid_ct_power`  | Grid CT L1 power (W)|
|grid_ct_power_L2: | Optional | `none`  | Grid CT L2 power (W)|
|grid_ct_power_L3: | Optional | `none`  | Grid CT L3 power (W)|
|pv1_voltage_109: | Optional | `sensor.sunsynk_pv1_voltage` | PV string 1 voltage (V) |
|pv1_current_110: | Optional | `sensor.sunsynk_pv1_current` | PV string 1 current (A)|
|pv2_voltage_111: | Optional | `sensor.sunsynk_pv2_voltage` | PV string 2 voltage (V)|
|pv2_current_112: | Optional | `sensor.sunsynk_pv2_current` | PV string 2 current (A)|
|pv3_voltage_113: | Optional | `sensor.sunsynk_pv3_voltage` | PV string 3 voltage (V) |
|pv3_current_114: | Optional | `sensor.sunsynk_pv3_current` | PV string 3 current (A)|
|pv4_voltage_115: | Optional | `sensor.sunsynk_pv4_voltage` | PV string 4 voltage (V)|
|pv4_current_116: | Optional | `sensor.sunsynk_pv4_current` | PV string 4 current (A)|
|grid_connected_status_194: | Optional | `binary_sensor.sunsynk_grid_connected_status` | Grid connected status `on/off`,`1/0` or `On-Grid/Off-Grid` |
|inverter_status_59: | Optional | `sensor.sunsynk_overall_state` | Inverter status `0, 1, 2, 3, 4` or `standby, selftest, normal, alarm, fault`. For Goodwe `0,1,2` or `idle, importing, exporting` |
|battery_status: | Optional | `sensor.battery_mode_code` | Used only when inverter model is set to  `goodwe`. Battery status `0, 1, 2, 3, 4` |
|aux_power_166: | Optional | `sensor.sunsynk_aux_power` | Auxilary power (W) |
|aux_load1:| Optional |  | Sensor that contains the power of your AUX load 1 (W) |
|aux_load2:| Optional |  | Sensor that contains the power of your AUX load 2 (W) |
|aux_connected_status: |Optional | | AUX Connected Status `on/off` or `1/0`
|remaining_solar: | Optional | `sensor.solcast_forecast_remaining_today`| The remaining solar forecast for the day (kWh). Use with solar `display_mode:2` |
|total_pv_generation: | Optional | | Total Solar generation (Lifetime or forecast for the day) (kWh). Use with solar `display_mode:3` |
|battery_temp_182:| Optional | `sensor.sunsynk_battery_temperature` | Battery temperature (℃)|
|radiator_temp_91:| Optional | `sensor.sunsynk_radiator_temperature` | Inverter AC temperature (℃)|
|dc_transformer_temp_90:| Optional | `sensor.sunsynk_dc_transformer_temperature` | Inverter DC temperature (℃)|
|prog1_time:| Optional | `sensor.sunsynk_time_slot_1` | Program 1 start time (`HH:MM`)
|prog1_capacity:| Optional | `number.sunsynk_system_mode_soc_time1` | Program 1 capacity (SOC) setting
|prog1_charge:| Optional | `switch.sunsynk_system_mode_grid_charge_time1` | Program 1 charge options (`on/off`, `1/0`, `No Grid or Gen`)
|prog2_time:| Optional | `sensor.sunsynk_time_slot_2` | Program 2 start time (`HH:MM`)
|prog2_capacity:| Optional | `number.sunsynk_system_mode_soc_time2` | Program 2 capacity (SOC) setting
|prog2_charge:| Optional | `switch.sunsynk_system_mode_grid_charge_time2` | Program 2 charge options (`on/off`, `1/0`, `No Grid or Gen`)
|prog3_time:| Optional | `sensor.sunsynk_time_slot_3` | Program 3 start time (`HH:MM`)
|prog3_capacity:| Optional | `number.sunsynk_system_mode_soc_time3` | Program 3 capacity (SOC) setting
|prog3_charge:| Optional | `switch.sunsynk_system_mode_grid_charge_time3` | Program 3 charge options (`on/off`, `1/0`, `No Grid or Gen`)
|prog4_time:| Optional | `sensor.sunsynk_time_slot_4` | Program 4 start time (`HH:MM`)
|prog4_capacity:| Optional | `number.sunsynk_system_mode_soc_time4` | Program 4 capacity (SOC) setting
|prog4_charge:| Optional | `switch.sunsynk_system_mode_grid_charge_time4` | Program 4 charge options (`on/off`, `1/0`, `No Grid or Gen`)
|prog5_time:| Optional | `sensor.sunsynk_time_slot_5` | Program 5 start time (`HH:MM`)
|prog5_capacity:| Optional | `number.sunsynk_system_mode_soc_time5` | Program 5 capacity (SOC) setting
|prog5_charge:| Optional | `switch.sunsynk_system_mode_grid_charge_time5` | Program 5 charge options (`on/off`, `1/0`, `No Grid or Gen`)
|prog6_time:| Optional | `sensor.sunsynk_time_slot_6` | Program 6 start time (`HH:MM`)
|prog6_capacity:| Optional | `number.sunsynk_system_mode_soc_time6` | Program 6 capacity (SOC) setting
|prog6_charge:| Optional | `switch.sunsynk_system_mode_grid_charge_time6` | Program 6 charge options (`on/off`, `1/0`, `No Grid or Gen`)
|energy_cost_buy:| Optional | | Sensor that provides current buy energy cost per kWh
|energy_cost_sell:| Optional | | Sensor that provides current sell energy cost per kWh
|solar_sell_247:|Optional | `switch.sunsynk_toggle_solar_sell` | Displays icons to indicate if sell solar is active or not. The switch can be toggled by clicking on the icon (`on/off`, `1/0`)

The card calculates the sensors below based on supplied attributes in the config so you dont need to define them in Home Assistant. NOTE if your essential and non-essential readings are innacurate replace sensor 169 with 167. Alternatively provide the card with sensors that calculate this data i.e essential_power: and nonessential_power:

 ```
 totalsolar = pv1_power_186 + pv2_power_187 + pv3_power_188 + pv4_power_189
 nonessential = grid_ct_power_172 - grid_power_169 (Single Phase)
 nonessential = grid_ct_power_172 + grid_ct_power_L2 + grid_ct_power_L3 - grid_power_169 (Three Phase)
 essential = inverter_power_175 + grid_power_169 - aux_power_166
 ```

The modbus registers can be visualised on the `full` card below:

![image](https://user-images.githubusercontent.com/7227275/235479493-b322d5b2-f2b1-431f-9048-f845fc2989b4.png)

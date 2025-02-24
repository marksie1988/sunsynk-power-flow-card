##########################
Solis Inverter Configuration
##########################

******************************************************************************************
Example 1 - Integration via https://github.com/wills106/homeassistant-solax-modbus
******************************************************************************************

.. code-block:: yaml
  :linenos:

    type: custom:sunsynk-power-flow-card
    cardstyle: lite
    show_solar: true
    large_font: true
    inverter:
      modern: true
      autarky: energy
    battery:
      energy: 14400
      shutdown_soc: 20
      full_capacity: 100
      empty_capacity: 20
      show_daily: true
    solar:
      show_daily: true
      mppts: 1
    load:
      show_daily: true
      additional_loads: 2
      load1_name: PC
      load1_icon: mdi:desktop-classic
      load2_name: TV
      load2_icon: mdi:television
    grid:
      show_daily_buy: true
      show_daily_sell: true
      show_nonessential: false
    entities:
      grid_power_167: sensor.solis_inverter_meter_active_power
      essential_power: sensor.solis_inverter_house_load
      essential_load1: sensor.pc_socket_power
      essential_load2: sensor.smart_socket_3_power
      energy_cost_buy: sensor.octopus_energy_electricity_xxxxx_xxxxxx_current_rate
      energy_cost_sell: sensor.octopus_energy_electricity_xxxxxx_xxxxx_export_current_rate
      remaining_solar: sensor.energy_production_today_remaining
      radiator_temp_91: sensor.solis_inverter_inverter_temperature
      use_timer_248: switch.sunsynk_toggle_system_timer
      inverter_voltage_154: sensor.solis_inverter_inverter_voltage
      load_frequency_192: sensor.solis_inverter_inverter_frequency
      inverter_current_164: sensor.solis_inverter_inverter_current
      inverter_power_175: sensor.solis_inverter_active_power
      day_battery_charge_70: sensor.solis_inverter_battery_charge_today
      day_battery_discharge_71: sensor.solis_inverter_battery_discharge_today
      battery_voltage_183: sensor.solis_inverter_battery_voltage
      battery_soc_184: sensor.solis_inverter_battery_soc
      battery_power_190: sensor.battery_load
      battery_current_191: sensor.solis_inverter_battery_current
      day_grid_import_76: sensor.solis_inverter_grid_import_today
      day_grid_export_77: sensor.solis_inverter_grid_export_today
      grid_ct_power_172: sensor.solis_inverter_meter_active_power
      day_load_energy_84: sensor.solis_inverter_house_load_today
      day_pv_energy_108: sensor.solis_inverter_power_generation_today
      pv1_power_186: sensor.solis_inverter_pv_total_power
      pv1_voltage_109: sensor.solis_inverter_pv_voltage_1
      pv1_current_110: sensor.solis_inverter_pv_current_1
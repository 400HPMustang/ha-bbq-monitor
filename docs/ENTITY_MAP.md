# Entity map

The repository is sanitized and does not contain private IP addresses or device-specific controller IDs.

## Inkbird LocalTuya entities expected by the YAML

| Purpose | Expected entity ID |
|---|---|
| DP107 raw packed probe temperatures | `sensor.ibbq_raw_probe_data` |
| DP111 probe-presence bitmask | `sensor.ibbq_probe_status_raw` |
| DP101 battery | `sensor.ibbq_battery` |
| DP104 mute | `switch.ibbq_mute` |
| DP19 temperature unit | `select.ibbq_temperature_unit` |

The templates create:

```text
sensor.ibbq_probe_1
sensor.ibbq_probe_2
sensor.ibbq_probe_3
sensor.ibbq_probe_4
binary_sensor.ibbq_probe_1_connected
binary_sensor.ibbq_probe_2_connected
binary_sensor.ibbq_probe_3_connected
binary_sensor.ibbq_probe_4_connected
```

## Pit Boss entities expected by the YAML

```text
climate.pit_boss_grill_temperature
binary_sensor.pit_boss_connectivity
binary_sensor.pit_boss_mpc_error
binary_sensor.pit_boss_p2_error
binary_sensor.pit_boss_p3_error
binary_sensor.pit_boss_startup_error
binary_sensor.pit_boss_high_temperature_error
binary_sensor.pit_boss_fan_error
binary_sensor.pit_boss_igniter_error
binary_sensor.pit_boss_auger_error
binary_sensor.pit_boss_no_pellets
```

The Pit Boss integration normally creates entity IDs containing a controller identifier. Rename those entities or replace the generic IDs in this repository.

## TTS

Defaults:

```text
media_player.all_homepods
script.stop_all_homepods
tts.google_translate_say
```

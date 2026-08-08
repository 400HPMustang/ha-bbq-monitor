# LocalTuya setup — Inkbird IBBQ-4T

These settings are for the IBBQ-4T variant that exposes all four probe temperatures packed into DP107.

## Manual DPS

Add `107` to **Manual DPS** if LocalTuya does not discover it automatically.

## DP107 — raw probe data

- Type: `sensor`
- Friendly name: `IBBQ Raw Probe Data`
- Unit: blank
- Device class: blank
- Scaling factor: blank
- Recommended entity ID: `sensor.ibbq_raw_probe_data`

## DP111 — probe status

- Type: `sensor`
- Friendly name: `IBBQ Probe Status Raw`
- Unit: blank
- Device class: blank
- Scaling factor: blank
- Recommended entity ID: `sensor.ibbq_probe_status_raw`

DP111 is an active-low bitmask:

| Value | Connected probes |
|---:|---|
| 15 | none |
| 14 | 1 |
| 13 | 2 |
| 11 | 3 |
| 7 | 4 |
| 0 | all four |

Other values represent combinations of multiple connected probes.

## DP101 — battery

- Type: `sensor`
- Friendly name: `IBBQ Battery`
- Unit: `%`
- Device class: `Battery`
- Scaling factor: **blank**
- Recommended entity ID: `sensor.ibbq_battery`

On the tested LocalTuya 5.2.3 setup, leaving scaling blank produced the correct percentage.

## DP104 — mute

- Type: `switch`
- Friendly name: `IBBQ Mute`
- Current: blank
- Current consumption: blank
- Voltage: blank
- Restore last value: unchecked
- Passive: unchecked
- Default value: blank
- Recommended entity ID: `switch.ibbq_mute`

## DP19 — Fahrenheit / Celsius

- Type: `select`
- Friendly name: `IBBQ Temperature Unit`
- Valid entries: `f;c`
- User-friendly options: `Fahrenheit;Celsius`
- Restore last value: unchecked
- Passive: unchecked
- Default: blank
- Recommended entity ID: `select.ibbq_temperature_unit`

## DPs intentionally ignored

DP1, DP102 and DP105 are not required for this project.

## Warning about reconfiguration

LocalTuya's reconfiguration wizard may walk through or disturb previously configured entities. Once the device works, prefer Home Assistant-side template changes over reconfiguring LocalTuya for cosmetic adjustments.

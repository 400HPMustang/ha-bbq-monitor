# What gets created

## Helpers

### Finish targets

```text
input_number.ibbq_target_probe_1
input_number.ibbq_target_probe_2
input_number.ibbq_target_probe_3
input_number.ibbq_target_probe_4
```

### Smoking profiles

```text
input_select.ibbq_probe_1_profile
input_select.ibbq_probe_2_profile
input_select.ibbq_probe_3_profile
input_select.ibbq_probe_4_profile
```

### Alert state / latches

```text
input_boolean.ibbq_probe_1_milestone_announced
input_boolean.ibbq_probe_2_milestone_announced
input_boolean.ibbq_probe_3_milestone_announced
input_boolean.ibbq_probe_4_milestone_announced
input_boolean.pit_boss_ready_armed
input_boolean.pit_boss_reached_temperature
```

## Template entities

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

## Automations

- IBBQ - Apply Probe Smoking Profile
- IBBQ - Probe Target Temperature Alerts
- IBBQ - Smoking Milestone Alerts
- IBBQ - Reset Smoking Milestones
- Pit Boss - Error Alerts
- Pit Boss - Smoker Ready
- Pit Boss - Temperature Problem

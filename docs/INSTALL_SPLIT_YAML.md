# Install using split YAML files

Use this method if your Home Assistant configuration already uses files such as `template.yaml`, `input_number.yaml`, etc.

## 1. configuration.yaml

Add these includes **only if you do not already have them**:

```yaml
input_number: !include input_number.yaml
input_select: !include input_select.yaml
input_boolean: !include input_boolean.yaml
template: !include template.yaml
```

If your automations are managed by the Home Assistant UI, do **not** replace your existing automation include. Create the automations through the UI using the files in `/automations/`.

## 2. Helpers

Merge the contents of:

```text
split_yaml/input_number.yaml
split_yaml/input_select.yaml
split_yaml/input_boolean.yaml
```

into your corresponding existing files.

These create four probe finish-temperature helpers, four smoking-profile selectors, four milestone latches, and the two Pit Boss ready-state helpers.

## 3. Templates

Merge `split_yaml/template.yaml` into your existing `template.yaml`.

This creates:

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

## 4. Automations

The `/automations/` directory contains each automation as a standalone YAML file formatted for **Settings → Automations & Scenes → Create Automation → Edit in YAML**.

Create/import:

1. `ibbq_apply_probe_smoking_profile.yaml`
2. `ibbq_probe_target_temperature_alerts.yaml`
3. `ibbq_smoking_milestone_alerts.yaml`
4. `ibbq_reset_smoking_milestones.yaml`
5. `pit_boss_error_alerts.yaml`
6. `pit_boss_ready_cycle.yaml`
7. `pit_boss_temperature_problem.yaml`

Alternatively, `split_yaml/automations.yaml` contains the same automations as one normal automation list.

## 5. Entity IDs

The repository uses sanitized generic IDs. Either rename your integration-created entities to match or search/replace them in the YAML. See `ENTITY_MAP.md`.

## 6. TTS

The automations assume:

```text
media_player.all_homepods
script.stop_all_homepods
tts.google_translate_say
```

Change those references to match your installation.

## 7. Dashboard

`dashboards/bbq_sections_view.yaml` is a complete YAML dashboard using Home Assistant's responsive Sections layout.

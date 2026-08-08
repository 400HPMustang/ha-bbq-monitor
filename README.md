# Home Assistant BBQ Monitor

A Home Assistant setup combining an **Inkbird IBBQ-4T** through LocalTuya with a **Pit Boss** smoker using [`dknowles2/ha-pitboss`](https://github.com/dknowles2/ha-pitboss).

This repository includes the complete Home Assistant side: LocalTuya DP notes, probe-decoding templates, helpers, smoking profiles, automations, HomePod TTS alerts, and a responsive Sections dashboard.

## Features

- Decodes all four IBBQ-4T probes from packed DP107
- Detects connected/disconnected probes from DP111
- Battery, mute, and °F/°C control
- Independent smoking profile and finish target for each probe
- One-time 165°F bark/wrap milestone for brisket and pork shoulder
- Finish-temperature announcements
- Pit Boss thermostat/setpoint control
- Pit Boss hardware/error/connectivity announcements
- Smoker-ready announcement
- Sustained high/low chamber-temperature warnings
- Responsive desktop/tablet/mobile dashboard

## Repository layout

```text
ha-bbq-monitor/
├── README.md
├── LICENSE
├── packages/
│   └── bbq_monitor.yaml
├── split_yaml/
│   ├── input_number.yaml
│   ├── input_select.yaml
│   ├── input_boolean.yaml
│   ├── template.yaml
│   └── automations.yaml
├── automations/
│   ├── ibbq_apply_probe_smoking_profile.yaml
│   ├── ibbq_probe_target_temperature_alerts.yaml
│   ├── ibbq_smoking_milestone_alerts.yaml
│   ├── ibbq_reset_smoking_milestones.yaml
│   ├── pit_boss_error_alerts.yaml
│   ├── pit_boss_ready_cycle.yaml
│   └── pit_boss_temperature_problem.yaml
├── dashboards/
│   └── bbq_sections_view.yaml
└── docs/
    ├── LOCAL_TUYA.md
    ├── PITBOSS.md
    ├── INSTALL_SPLIT_YAML.md
    ├── ENTITY_MAP.md
    ├── WHAT_GETS_CREATED.md
    └── SECURITY.md
```

## Installation option 1: one complete Home Assistant package

Copy `packages/bbq_monitor.yaml` to `/config/packages/` and enable packages if necessary:

```yaml
homeassistant:
  packages: !include_dir_named packages
```

That single package contains **all helpers, template entities, and automations**.

## Installation option 2: split YAML / existing Home Assistant config

If you already use `input_number.yaml`, `input_select.yaml`, `input_boolean.yaml`, and `template.yaml`, use the files under `split_yaml/`.

The `automations/` directory contains each automation separately in the same format you can paste into Home Assistant's **Edit in YAML** automation editor.

See [`docs/INSTALL_SPLIT_YAML.md`](docs/INSTALL_SPLIT_YAML.md).

## IBBQ-4T LocalTuya setup

See [`docs/LOCAL_TUYA.md`](docs/LOCAL_TUYA.md).

Tested DPs:

| DP | Purpose |
|---:|---|
| 19 | °F / °C selection |
| 101 | Battery |
| 104 | Mute |
| 107 | Packed four-probe temperatures |
| 111 | Connected-probe bitmask |

DP107 may need to be entered under LocalTuya **Manual DPS**.

## Generic entity IDs

This repo is sanitized. See [`docs/ENTITY_MAP.md`](docs/ENTITY_MAP.md) for the generic IDs expected by the YAML and what to rename/search-replace.

## Smoking profiles

| Profile | Finish target |
|---|---:|
| Brisket | 203°F |
| Pork Shoulder / Butt | 203°F |
| Beef Chuck Roast | 203°F |
| Chicken Wings | 175°F |
| Chicken Thighs | 175°F |
| Chicken Breast | 165°F |
| Turkey Breast | 165°F |
| Pork Tenderloin | 145°F |
| Sausage - Beef/Pork | 160°F |
| Sausage - Poultry | 165°F |
| Manual | User controlled |

Brisket and pork shoulder also get a one-time 165°F notification to check bark / consider wrapping.

## TTS

Examples use:

```text
media_player.all_homepods
script.stop_all_homepods
tts.google_translate_say
```

Change them to suit your installation.

## Smoker-ready behavior

The packaged ready automation includes the fix discovered during live testing: it must first observe the smoker at least **15°F below the target** before arming. Reloading Home Assistant while the smoker is already at temperature will therefore not generate a bogus "smoker ready" announcement.

## License

MIT. Use it, modify it, fork it, redistribute it.

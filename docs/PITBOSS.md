# Pit Boss integration notes

Tested with:

https://github.com/dknowles2/ha-pitboss

The climate entity is used for:

- actual chamber temperature: `current_temperature`
- chamber setpoint: `temperature`

The setup also uses dedicated binary sensors for:

- connectivity
- MPC / meat-probe error
- P2 error
- P3 error
- startup error
- high-temperature error
- fan error
- igniter error
- auger error
- no-pellets error

Your model/controller may expose a different set of entities.

The dashboard thermostat card shows:

- large number = setpoint
- smaller number = current chamber temperature
- +/- = setpoint control

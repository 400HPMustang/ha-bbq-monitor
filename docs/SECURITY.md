# Security checklist

Do not commit:

- Tuya `local_key`
- Tuya device IDs if you prefer to keep them private
- Home Assistant long-lived access tokens
- API keys
- private IP addresses
- Wi-Fi SSIDs/passwords
- `secrets.yaml`
- Home Assistant `.storage/`
- backups containing secrets
- personally identifying device names

Use Home Assistant `secrets.yaml` for credentials whenever possible.

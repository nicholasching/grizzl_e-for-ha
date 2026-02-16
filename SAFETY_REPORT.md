# Safety Report

## Summary

Based on this repository's code, the integration communicates directly from your Home Assistant instance to your Grizzl-E charger on your local network.

**Will the repository owner gain access to your data?**  
No evidence in this code indicates data is sent to the repository owner.

**Will third parties gain access to your data?**  
No evidence in this code indicates telemetry, analytics, or cloud upload to third parties.

## What data is used

The integration stores and uses:
- Charger host/IP address
- Charger username and password
- Charger status/metrics returned by the charger (power, energy, temperatures, state, firmware versions, etc.)

## Where data is sent

From the code in this repository:
- Requests are sent to `http://<your_charger_host>/main` using HTTP Basic Auth.
- Polling is local (`"iot_class": "local_polling"` in `manifest.json`).
- There are no configured external API endpoints in the integration code.

## Important caveats

- Credentials are entered into Home Assistant and stored by Home Assistant's config entry system on your own HA instance.
- Communication to the charger is HTTP (not HTTPS), so network-level exposure depends on your local network security.
- If you install updates through GitHub/HACS, those platforms have their own privacy policies, but this integration code itself does not upload charger telemetry to them.

## Practical recommendations

- Keep your charger on a trusted local network.
- Set a strong charger password and avoid defaults.
- Restrict remote access to Home Assistant and your LAN.

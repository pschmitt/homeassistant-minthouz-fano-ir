<p align="center">
  <img src="docs/images/fano-p12l.webp" width="180" alt="Minthouz Fano P12L clip fan">
</p>

<p align="center">
  <a href="https://my.home-assistant.io/redirect/marketplace_repository/?owner=pschmitt&amp;repository=homeassistant-minthouz-fano-ir&amp;category=integration"><img src="https://my.home-assistant.io/badges/marketplace_repository.svg" alt="Open this integration in Home Assistant Marketplace"></a>
</p>

<h1 align="center">Minthouz Fano P12L Fan (IR)</h1>

<p align="center">Control a Minthouz clip fan through an existing Home Assistant infrared emitter.</p>

This unofficial integration uses the fan's NEC-IR remote codes and an
`infrared.*` entity; it does not communicate with the fan directly. It
requires Home Assistant 2026.3.0 or later.

## Features

- **Fan control:** Turn power on or off and choose among three speeds.
- **LED and timers:** Cycle three LED brightness levels and trigger two-, four- or six-hour timer presets.
- **Emitter choice:** Use any compatible `infrared.*` emitter, including an ESPHome IR blaster. See [Infrared controls](docs/ir-controls.md).
- **Assumed state:** Work around the remote's missing feedback for reliable fan power commands.

## Install

Use the Marketplace badge above on Home Assistant 2026.11 or later to add this
repository as a custom integration. On older versions (2026.3 or later), add
it as a HACS custom repository of type **Integration**. Install and restart
Home Assistant. The badge does not imply a public catalog listing. For manual
installation, copy `custom_components/minthouz_fano/` into Home Assistant's
`custom_components/` directory and restart.

## Quick start

1. Set up a compatible `infrared.*` emitter in Home Assistant.
2. Add **Minthouz Fano P12L Fan (IR)** under **Settings → Devices & services → Add integration**.
3. Select the emitter and use the fan, light and timer entities.

## Documentation

| Topic | Description |
|-------|-------------|
| [Infrared controls](docs/ir-controls.md) | Remote behavior, entity state and an ESPHome emitter example |

## License

[GPL-3.0](LICENSE).

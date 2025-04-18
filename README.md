# homeassistant-uponor

<a href="https://www.buymeacoffee.com/davecoderuiz" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-orange.png" alt="Buy Me A Coffee" height="41" width="174"></a>

[![hacs_badge](https://img.shields.io/badge/HACS-Default-orange.svg)](https://github.com/hacs/integration)
[![hacs_badge](https://img.shields.io/badge/HACS-Custom-orange.svg)](https://github.com/hacs/integration)

Uponor Smatrix Pulse X-265 R-208 heating/cooling integration for Home Assistant.

## First Note

I create this repo beause repo https://github.com/asev/homeassistant-uponor is deprecated and I have no news from the creator @asev

## Supported devices

This integration communicates with Uponor Smatrix Pulse communication module R-208.
It should work with all controllers that support this module.

## Installation

1. Setup and configure your system on Uponor Smatrix mobile app. Make sure you are able to control temperature via the app.
Your Uponor has to be connected to the local network and you should know it's IP address.

2. Install "Uponor Smatrix X-265 module R-208" integration on HACS

OR copy the custom_components folder to your own Home Assistant /config folder.

3. Restart Home Assistant server

4. Go to Configuration > Integration" > Add Integration > UponorX265. Finish the setup.
   
## Structure

Separate entity `climate.THERMOSTAT_NAME` will be created for every thermostat.
Each thermostat will be registered as a separate device. Also one device will be registered for entire system.

`switch.uponor_away` controls away mode. It activates ECO mode for all thermostat.

`switch.uponor_cooling_mode` activates cooling mode when switched on and heating mode when it's switched off.
This switch will be added only if cooling is available in your system.

`uponor.set_variable` service allows to send POST requests to Uponor API. Use it with caution!

### Climate entity

Climate entity has read-only preset. Two presets are available:
* ECO - activated when scheduled ECO profile is on OR Temporary ECO mode activated on the mobile app.
* Away - activated when `switch.uponor_away` is on.

If none of those are true, then preset is empty.

## Limitations

Uponor API doesn't support heat/cool switch for single thermostat.
`switch.uponor_cooling_mode` change mode for entire system.

Uponor API does not support turn off action. When climate entity is turned off on Home Assistant,
the temperature is set to the minimum (default 5℃) when heating mode is active
and to the maximum (default 35℃) when cooling mode is active.

## Older module

In case you have older Uponor X-165 module visit: https://github.com/dave-code-ruiz/uhomeuponor

## Feedback

Your feedback, pull requests or any other contribution are welcome.

# ESP32 + SvelteKit

The an example of serving a SvelteKit app from an ESP32 microcontroller.

Tested with a [WROOM-32 devkit](https://abra-electronics.com/robotics-embedded-electronics/esp-series/wifi-esp32-esp-wroom-32-wi-fi-bluetooth-ble-low-power-iot-microcontroller.html)

## Background

- The SvelteKit app is build with the `@sveltejs/static-adapter`.
- The `build` directory is synced to the flash using `rshell`. Thankfully Svelte bundles are very small, and can fit inside the microcontroller's flash. For larger projects, you can use an SD card.
- The `firmware` folder contains the Python code to connect to WIFI, and start a WebServer. Just copy it over to the ESP32 using `rshell`.

## Setup

```sh
# install the rshell cli
pip install rshell

# connect to ESP32
rshell connect serial /dev/ttyUSB0

# copy firmware to device
rshell rsync firmware /pyboard

# build svelte-kit project
pnpm build

# copy `build` folder to device
rshell rsync build /pyboard/build
```

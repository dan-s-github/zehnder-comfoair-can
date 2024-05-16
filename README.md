# Zehnder Comfoair Q ESPHome

This project uses the [m5stack ATOM Lite](https://shop.m5stack.com/products/atom-lite-esp32-development-kit) Controller as core component

  ![m5stack_atom]

either as part of the [m5stack Canbus Kit](https://shop.m5stack.com/products/atom-canbus-kit-ca-is3050g) to interact with the Zehnder ComfoAir Q ventilation unit 

  ![m5stack_can]

or using a custom pcb based on [vekexasia](https://github.com/vekexasia/comfoair-esp32/issues/49#issuecomment-1578201546) schematics. 
All required manufaturing documents have been added to [docs/pcb](docs/pcb/)

  ![custom_bare]

Sourcecode is based on this repo: https://github.com/yoziru/esphome-zehnder-comfoair which uses an [Olimex ESP32-EVB](https://github.com/OLIMEX/ESP32-EVB) with CAN interface.

Needs at least ESPHome 2022.5.0 (since it depends on some CAN bus component updates).

- It exposes all known information and airflow control through the [ESPHome native API](https://esphome.io/components/api.html).
- It allows you to integrate the unit in Home Assistant as depicted below using following custom card:
    - `custom:fold-entity-row`

  ![Home Assistant closed][ha_dashboard_top]

  I now use the thermostat card instead of the `custom:mushroom-climate-card`

  ![Home Assistant thermostat][ha_dashboard_thermostat]

  ![Home Assistant open][ha_dashboard_bottom]
 
You can find the sample configuration YAML and image in the [`docs/home-assistant`](docs/home-assistant/) folder.

## Components

- m5stack Atom Lite
- one of the Hardware options
- Any ethernet cable (RJ45 connector) or a 4 core cable
- A USB-C cable to connect the m5stack Atom Lite to your computer

### Prepare Atom Lite

This uses esphome to prepare the atom lite for home assistant

1. Navigate to [ESPHome Web Installer](https://web.esphome.io/)
2. `Connect` to your device
3. `Prepare for first use`
4. `Install`
5. wait until configuration has been installed
6. `Connect to Wi-Fi`

### Install Software

1. Navigate to ESPHome in [Home Assistant](http://homeassistant.local:8123/) 
2. `ADOPT` newly initialised device
    ![ESPHome Discovered][esphome_adopt]
    - Specify name for new device
      - `Zehnder ComfoAir ESP32`
    - `ADOPT`
3. `Install` to add encryption key to device
    - Close dialog after image has been uploaded succesfully

4. The device will still use the inital hostname which is also the name of the yaml file stored in home assistant. Renaming the hostname using ESPHome Dashboard will also update the yaml filename to reflect the changed hostname.
    
    - Use `rename hostname` in the options dialog of the adopted device
      ![ESPHome rename hostname][esphome_rename]
    - `RENAME`
      - Close dialog after image has been uploaded succesfully

5. Device is now ready for customization
 ![ESPHome ready][esphome_ready]

6. Use the [zehnder-comfoair-can.yaml](zehnder-comfoair-can.yaml) as template to edit your newly created yaml file

### Hardware

 Option 1: [Using m5stack Can bus kit](M5STACK_CAN_BUS_KIT.md)
 
  ![m5stack_can][m5stack_can]

 Option 2: [Using custom pcb](CUSTOM_PCB.md)

  ![custom_atom][custom_atom]

## Credits

Based on https://github.com/yoziru/esphome-zehnder-comfoair which uses an [Olimex ESP32-EVB](https://github.com/OLIMEX/ESP32-EVB) with CAN interface.

Inspired by

- https://github.com/vekexasia/comfoair-esp32
- https://github.com/michaelarnauts/aiocomfoconnect
- https://github.com/felixstorm/esphome-custom-components
- [https://github.com/mat3u/comfoair-esp32](https://github.com/mat3u/comfoair-esp32/tree/hacomfoairmqtt-compatibility)
- [https://github.com/hcouplet/comfoair-esp32](https://github.com/hcouplet/comfoair-esp32/tree/hacomfoairmqtt-compatibility)

A lot of this repo was inspired by the reverse engineering [here](https://github.com/marco-hoyer/zcan/issues/1).

- [ComfoControl Protocol](https://github.com/michaelarnauts/aiocomfoconnect/blob/master/docs/PROTOCOL.md)
- [RMI PROTOCOL](https://github.com/michaelarnauts/aiocomfoconnect/blob/master/docs/PROTOCOL-RMI.md)
- [PDO PROTOCOL](https://github.com/michaelarnauts/aiocomfoconnect/blob/master/docs/PROTOCOL-PDO.md)

[ha_dashboard_top]: ./docs/ha_dashboard_top.png
[ha_dashboard_bottom]: ./docs/ha_dashboard_bottom.png
[ha_dashboard_thermostat]: ./docs/ha_dashboard_thermostat.png

[m5stack_atom]: ./docs/m5stack_atom.png
[m5stack_can]: ./docs/m5stack_can_kit.png

[custom_bare]: ./docs/custom_pcb_bare.png
[custom_atom]: ./docs/custom_pcb_incl_atom.png

[esphome_adopt]: ./docs/esphome_adopt.png
[esphome_rename]: ./docs/esphome_rename.png
[esphome_ready]: ./docs/esphome_ready.png

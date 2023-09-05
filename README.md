# Zehnder Comfoair Q ESPHome

This project uses the [m5stack Canbus Kit](https://shop.m5stack.com/products/atom-canbus-kit-ca-is3050g) to interact with the Zehnder ComfoAir Q ventilation unit.

  ![M5STACK CAN][m5stack_can]

It is based on this repo: https://github.com/yoziru/esphome-zehnder-comfoair which uses an [Olimex ESP32-EVB](https://github.com/OLIMEX/ESP32-EVB) with CAN interface.

Needs at least ESPHome 2022.5.0 (since it depends on some CAN bus component updates).

- It exposes all known information and airflow control through the [ESPHome native API](https://esphome.io/components/api.html).
- It allows you to integrate the unit in Home Assistant as depicted below using following custom cards:
    - custom:mushroom-climate-card
    - custom:fold-entity-row


  ![Home Assistant closed][ha_dashboard_top]

  ![Home Assistant open][ha_dashboard_bottom]
 
You can find the sample configuration YAML and image in the [`docs/home-assistant`](docs/home-assistant/) folder.

## Components

- m5stack Canbus Kit
- 5V power supply adapter
- Any ethernet cable (RJ45 connector)
- A micro USB cable to connect the m5stack Atom Lite to your computer

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

6. Use the [zehnder-comfoair-esp32.yaml](zehnder-comfoair-esp32.yaml) as template to edit your newly created yaml file

To be continued...    

[ha_dashboard_top]: ./docs/ha_dashboard_top.png
[ha_dashboard_bottom]: ./docs/ha_dashboard_bottom.png
[m5stack_can]: ./docs/m5stack.png
[esphome_adopt]: ./docs/esphome_adopt.png
[esphome_rename]: ./docs/esphome_rename.png
[esphome_ready]: ./docs/esphome_ready.png

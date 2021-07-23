# AM43 component for ESPHome

This repo works as an [external component](https://esphome.io/components/external_components.html) for ESPHome to support the AM43
style blind/shade motors.

To use, add the following to your ESP32 device YAML. Change names,
IDs and mac_address to suit your setup.

Up to 3 AM43s are supported.

```
external_components:
  - source: github://buxtronix/esphome-am43

esp32_ble_tracker:

ble_client:
  - mac_address: 02:4D:FB:F0:5B:2E
    id: kitchen_am43

cover:
  - platform: am43
    name: "Kitchen Blinds"
    id: kitchen_cover
    ble_client_id: kitchen_am43

sensor:
  - platform: am43
    ble_client_id: kitchen_am43
    battery_level:
      name: "Kitchen AM43 battery"
    illuminance:
      name: "Kitchen AM43 light"
    update_interval: 120s

switch:
  - platform: ble_client
    name: "Kitchen window"
    ble_client_id: kitchen_am43

```


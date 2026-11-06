# Low-Power Tracking Tag

A compact, rechargeable Bluetooth tracking tag designed to be detected and ranged by multiple fixed stations.

## Project goals

- **Wireless:** Bluetooth 6.0 Channel Sounding (CS) for station-to-tag ranging
- **Power:** Low-power, rechargeable battery operation
- **Update interval:** Approximately once per minute
- **Environment:** Indoor and outdoor operation
- **Cost:** Low-cost tag and station hardware
- **Range:** Long-range coverage is a goal; operation beyond 100 m requires field validation
- **Accuracy:** Approximate location / nearest-station detection is sufficient

## Proposed hardware

**Tag:** Raytac AN54LV-U15 (Nordic nRF54L15), external 2.4 GHz u.FL antenna, protected 1-cell LiPo battery, charging IC, and 3.0 V low-quiescent-current regulator.

**Station:** nRF54L15 CS initiator with optional ESP32-C3 Wi-Fi backhaul to a central controller.

The tag is a CS reflector. Stations coordinate measurements and forward distance estimates to the controller. Battery life, reliable range, antenna performance, and station scheduling still need to be tested.

## Documents

- [Bill of materials](hardware/rechargeable_ble_tag_bom_tree.xlsx) — editable hierarchical BOM with supplier-link fields
- [System requirements](docs/requirements.md) — operating goals and prototype validation criteria

## Project status

**Early hardware planning.** Firmware, schematics, PCB layout, and field tests are not yet completed.

## Development tools

- Nordic nRF Connect SDK / Zephyr
- C for embedded firmware
- KiCad for schematic and PCB design

## Next steps

1. Select the LiPo battery, charger configuration, and antenna.
2. Prototype a station and tag using nRF54L15 development hardware.
3. Verify CS ranging with multiple stations and measure tag power consumption.
4. Design the compact tag PCB and enclosure.

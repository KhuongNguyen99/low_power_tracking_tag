# Rechargeable Tag BOM (initial draft)

This is the sourcing checklist for **one tag**. Confirm electrical values, footprints, and datasheet requirements before ordering or manufacturing. Paste supplier URLs into the blank **Material link** column as components are selected.

| ID | Assembly | Item | Qty | Suggested part / specification | Material link |
|---|---|---|---:|---|---|
| 1.1 | Radio | BLE 6.0 CS module | 1 | Raytac AN54LV-U15 | |
| 1.2 | Radio | External antenna | 1 | 2.4 GHz, u.FL mating connector; confirm exact connector | |
| 2.1 | Battery | Protected 1S LiPo | 1 | 3.7 V nominal, 4.2 V maximum; capacity TBD | |
| 2.2 | Battery | Battery connector | 1 | Match selected pack pitch **and polarity** | |
| 2.3 | Power | Low-Iq 3.0 V LDO | 1 | TI TPS7A0230 variant; verify footprint/current | |
| 2.4 | Power | LDO input capacitor | 1 | 1 µF X7R, per TI datasheet | |
| 2.5 | Power | LDO output capacitor | 1 | 1 µF X7R, per TI datasheet | |
| 2.6 | Power | On/off switch | 1 | Small SPST slide switch | |
| 3.1 | Charging | USB-C receptacle | 1 | 5 V power sink, power-only | |
| 3.2 | Charging | LiPo charging IC | 1 | MCP73831 4.2 V variant | |
| 3.3 | Charging | Charge current resistor | 1 | Value chosen for final battery and charger datasheet | |
| 3.4 | Charging | Charger supply capacitor | 1 | 4.7 µF, final value per reference circuit | |
| 3.5 | Charging | Charger battery capacitor | 1 | 4.7 µF, final value per reference circuit | |
| 3.6 | Charging | USB-C CC1 pulldown | 1 | 5.1 kΩ | |
| 3.7 | Charging | USB-C CC2 pulldown | 1 | 5.1 kΩ | |
| 3.8 | Charging | USB-C input TVS | 1 | Optional, appropriately rated | |
| 3.9 | Charging | Charge status LED + resistor | 1 set | Optional | |
| 4.1 | Radio support | DC/DC inductor | 1 | 4.7 µH; confirm Raytac schematic and footprint | |
| 4.2 | Radio support | VDD bypass capacitor | 1 | 4.7 µF; confirm Raytac schematic | |
| 4.3 | Radio support | 32.768 kHz LF crystal | 1 | Recommended unless firmware uses supported RC option | |
| 4.4 | Radio support | LF crystal load capacitors | 2 | Match crystal load capacitance and PCB parasitics | |
| 5.1 | Programming | SWDIO / SWDCLK / RESET / VTref / GND test pads | 1 set | For external debugger | |
| 5.2 | PCB | Custom carrier PCB | 1 | Module pad footprint and antenna clearance per Raytac | |
| 5.3 | Mechanical | Tag enclosure | 1 | Compact, nonmetallic RF window, suitable ingress protection | |

**Important:** The charger listed here is a simple linear charger without system power-path control. For operation while charging, redesign charging/power-path circuitry (for example with an appropriate power-path charger). A bare LiPo cannot connect directly to the AN54LV-U15 because 4.2 V exceeds its 3.6 V maximum.

## Reference links

- [Raytac AN54LV-U15](https://www.raytac.com/product/ins.php?index_id=176)
- [Raytac documentation](https://www.raytac.com/document/)
- [TI TPS7A02](https://www.ti.com/product/TPS7A02)
- [Microchip MCP73831](https://www.microchip.com/en-us/product/MCP73831)

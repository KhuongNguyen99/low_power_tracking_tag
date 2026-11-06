# Requirements and system concept

## Functional requirements

| ID | Requirement | Initial target |
|---|---|---|
| FR-01 | Battery-powered mobile tag | Rechargeable single-cell LiPo |
| FR-02 | Ranging technology | Bluetooth 6.0 Channel Sounding |
| FR-03 | Station configuration | Multiple fixed stations with known positions |
| FR-04 | Measurement frequency | Approximately every 60 seconds |
| FR-05 | Operating environments | Indoors and outdoors, using suitable enclosures |
| FR-06 | Measurement accuracy | Coarse ranging sufficient; prioritize reliability |
| FR-07 | Communication distance | Greater than 100 m desired; **unverified with CS** |
| FR-08 | Form factor | Compact wearable/attachable tag |
| FR-09 | System cost | Minimize tag and station component cost |
| FR-10 | Data collection | Stations forward tag ID, range, and measurement health to server |

## Proposed architecture

```text
Rechargeable tag (nRF54L15, CS reflector)
       |    |    |
       | BLE Channel Sounding connections
       v    v    v
  Station A   Station B   Station C ...
   nRF54L15 CS initiators
       | Wi-Fi / wired backhaul
       v
   Central controller: nearest-station or approximate-position estimation
```

Channel Sounding requires a compatible BLE connection and coordinated scheduling; BLE advertising alone does not produce CS distance estimates. Station connectivity and measurement intervals must be tested with battery-powered tag sleep modes.

## Initial tag design

- Raytac AN54LV-U15 programmable nRF54L15 radio module
- External 2.4 GHz antenna with matching u.FL connector
- 1S protected LiPo battery and matching connector
- 3.0 V low-quiescent-current regulator (LiPo voltage can reach 4.2 V)
- USB-C input and MCP73831 single-cell charger for a simple charge-while-off implementation
- Raytac-recommended DC/DC supply support, LF clock strategy, decoupling
- SWD programming pads

**Safety/design gate:** Confirm battery protection, polarity, charger current, charge temperature restrictions, USB-C input protection, and PCB layout against manufacturer datasheets. The proposed simple charger has no power-path management; don't assume simultaneous charging and normal ranging is supported.

## Prototype validation plan

1. Run Nordic nRF Connect SDK CS initiator/reflector samples on compatible development hardware.
2. Record success rate, 95th-percentile ranging error, and outlier frequency indoors and outdoors.
3. Test 10 m, 30 m, 50 m, 100 m, and beyond 100 m where practical; long-range BLE advertising does not establish CS range.
4. Validate two or more sequential station ranging sessions and synchronization after tag sleep.
5. Measure charge current, sleep current, ranging current, and peak radio current on final hardware.
6. Confirm antenna/enclosure performance and weather resistance.

## Reference documentation

- [Raytac module](https://www.raytac.com/product/ins.php?index_id=176)
- [Raytac documents](https://www.raytac.com/document/)
- [Nordic nRF Connect SDK documentation](https://docs.nordicsemi.com/bundle/ncs-latest/page/nrf/index.html)
- [TI TPS7A02](https://www.ti.com/product/TPS7A02)
- [Microchip MCP73831](https://www.microchip.com/en-us/product/MCP73831)

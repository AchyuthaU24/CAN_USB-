# Candlelight Rebuild — CAN Bus Interface PCB

A KiCad redesign of the open-source **Candlelight** USB-CAN adapter, rebuilt as a clean hierarchical multi-sheet schematic with a production-ready 2-layer PCB layout.

---

## Overview

This project is a from-scratch PCB rebuild of the Candlelight USB↔CAN interface, widely used in automotive and robotics applications. The design is organized as a hierarchical KiCad schematic split across five functional sheets, with the full PCB layout completed in KiCad PCB editor.

**Key specs:**
- MCU: STM32F072C8Tx (ARM Cortex-M0, 48 MHz, 64 KB Flash, 16 KB RAM, LQFP48)
- CAN Transceiver: TJA1051TK/3 (NXP High-Speed CAN, silent mode, VSON-8)
- Power: MCP1754S-3302 LDO (3.3 V, 150 mA, SOT-89)
- Interface: DB9 (DE-9) connector + pin headers (1×6, 1×10)
- Layers: 2-layer PCB, 1.6 mm stackup
- Nets: ~426 | Components: 40 footprints
- Tools used: KiCad 7/8

---

## Schematic Sheets

| Sheet | Contents |
|---|---|
| Root | Top-level hierarchy, sheet instantiation |
| MCU | STM32F072C8Tx, crystal, decoupling caps, test points |
| CAN | TJA1051TK/3 transceiver, termination resistors, bypass caps |
| Power | MCP1754S LDO regulator, input/output filtering, PWR_FLAG ERC compliance |
| LEDs | Status LEDs with current-limiting resistors |
| Connectors | DB9 (male), 6-pin and 10-pin headers |

---

## File Structure

```
candlelight_rebuild/
├── candlelight_rebuild.kicad_pro    # Project file
├── candlelight_rebuild.kicad_sch    # Root schematic
├── mcu.kicad_sch                    # MCU sub-sheet
├── mcu1.kicad_sch                   # MCU (alternate/updated)
├── CAN.kicad_sch                    # CAN transceiver sub-sheet
├── power.kicad_sch                  # Power regulation sub-sheet
├── leds.kicad_sch                   # LED indicators sub-sheet
├── connectors.kicad_sch             # Connectors sub-sheet
└── candlelight_rebuild.kicad_pcb    # PCB layout
```

---

## Getting Started

1. Install [KiCad 10](https://www.kicad.org/download/)
2. Clone this repo
3. Open `candlelight_rebuild.kicad_pro` in KiCad
4. Use **Schematic Editor** to view/edit schematics
5. Use **PCB Editor** to view/modify the board layout

---

## Design Notes

- Hierarchical labels used for clean inter-sheet connectivity (CAN_TX, CAN_RX, CAN_SD, CAN_H, CAN_L)
- Teardrop fill enabled on all pads and vias for manufacturing reliability
- ERC rule severities configured for strict unconnected pin checking
- 0.2 mm min track width, 0.05 mm min clearance design rules set

---

## Reference / Based On

- Original Candlelight firmware: [candle-usb/candleLight_fw](https://github.com/candle-usb/candleLight_fw)
- STM32F072 datasheet: [ST.com](https://www.st.com/en/microcontrollers-microprocessors/stm32f072c8.html)
- TJA1051 datasheet: [NXP](https://www.nxp.com/docs/en/data-sheet/TJA1051.pdf)

---

## License

This design is released under [CERN-OHL-S v2](https://ohwr.org/cern_ohl_s_v2.txt).

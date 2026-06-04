# STM32F405 Quadcopter Flight Controller
A custom 4-layer flight controller PCB designed from scratch in KiCad, targeting Betaflight compatibility with 4S–6S LiPo input. Designed, laid out, and submitted for SMT assembly through JLCPCB.

## Specifications
| Parameter | Detail |
|---|---|
| Microcontroller | STM32F405RGTx — ARM Cortex-M4 @ 168 MHz |
| Input Voltage | 4S–6S LiPo (14.8V–25.2V) |
| Power Architecture | TPS54360DDA Buck (5V/3.5A) → SPX3819 LDO (3.3V) |
| IMU | ICM-42688-P (SPI1, 6-DOF, 32kHz ODR) |
| Barometer | BMP388 (SPI3) |
| Magnetometer | QMC5883L (I2C2) |
| GPS | SAM-M10Q-00B (UART3, integrated antenna) |
| OSD | AT7456E with 27MHz crystal |
| USB | USB-C with USBLC6-2SC6 ESD protection |
| PCB | 4-Layer, 74×108mm, FR4 TG135, LeadFree HASL |
| Motor Outputs | 4× DShot (TIM1 CH1-3, TIM8 CH4) |
| Assembly | JLCPCB SMT — 43 component BOM |

## Repository Structure

    Hardware/
        Schematic/     — KiCad schematic files
        PCB/           — KiCad PCB layout files
        Gerbers/       — Fabrication files for JLCPCB
    BOM/               — Bill of materials with LCSC part numbers
    Docs/              — Full design portfolio PDF

## Design Portfolio
A full design portfolio documenting every schematic section, PCB layout decision, component selection rationale, and datasheet calculations is available below.

[📄 View Full Design Portfolio (PDF)](Docs/STM32_Drone_FC_Portfolio.pdf)

## Key Design Decisions
- 4-layer stackup: F.Cu (signals) / In1.Cu (GND plane) / In2.Cu (signal overflow) / B.Cu (3.3V distribution)
- Switched node area minimized around TPS54360 to reduce EMI
- Decoupling capacitors placed within 1–2mm of every power pin
- Ground via stitching at all signal layer transitions
- Magnetometer placed at maximum distance from power section
- USBLC6-2SC6 placed immediately at USB-C connector before any D+/D− routing

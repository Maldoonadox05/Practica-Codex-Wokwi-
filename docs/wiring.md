# Wiring and GPIO Mapping

## Components (derived from diagram)
- 1x Raspberry Pi Pico / Pico W
- 1x 4x4 membrane keypad
- 12x LEDs
  - 8x blue LEDs (labels 1..8)
  - 4x red LEDs (labels A..D)
- 12x 220Ω resistors (LED current limiting)
- 4x 1kΩ resistors (keypad row pull-ups to 3V3)
- Jumper wires

## Keypad Connections

| Keypad Pin | Pico W GPIO | Purpose |
|---|---:|---|
| C1 | GP19 | Column input/output (library scan) |
| C2 | GP18 | Column input/output (library scan) |
| C3 | GP17 | Column input/output (library scan) |
| C4 | GP16 | Column input/output (library scan) |
| R1 | GP26 | Row input/output (library scan) |
| R2 | GP22 | Row input/output (library scan) |
| R3 | GP21 | Row input/output (library scan) |
| R4 | GP20 | Row input/output (library scan) |

Additional row biasing in diagram:
- R1..R4 each tied to 3V3 through 1kΩ pull-up network.

## LED Connections
All LED cathodes connect to common GND.
Each LED anode connects through a 220Ω resistor to a Pico W GPIO.

| Logical LED | Key Label | Pico W GPIO |
|---|---|---:|
| LED1 | 1 | GP11 |
| LED2 | 2 | GP10 |
| LED3 | 3 | GP9 |
| LED4 | 4 | GP8 |
| LED5 | 5 | GP7 |
| LED6 | 6 | GP6 |
| LED7 | 7 | GP5 |
| LED8 | 8 | GP4 |
| LED9 | A | GP3 |
| LED10 | B | GP2 |
| LED11 | C | GP28 |
| LED12 | D | GP27 |

## Notes / Assumptions
- The source targets generic GPIO numbering and maps correctly to RP2040 pins.
- Despite using Pico W hardware, no wireless circuitry is used in this firmware.

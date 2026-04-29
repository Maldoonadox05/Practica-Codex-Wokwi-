# Pico W Keypad-to-LED Controller

A Raspberry Pi Pico W project that reads a 4x4 membrane keypad and controls 12 discrete LEDs. The firmware maps numeric and symbol keys to individual or grouped LED actions.

> **Important:** The provided source uses **Arduino-style APIs** (`setup()`, `loop()`, `digitalWrite()`, `Keypad` library). Logic is preserved as-is.

## Repository Structure

```text
.
├── CMakeLists.txt
├── diagram.json
├── docs/
│   ├── architecture.md
│   └── wiring.md
├── include/
└── src/
    └── main.cpp
```

## Features
- 4x4 keypad input scanning via `Keypad` library
- 12 independent GPIO-controlled LEDs
- Group control keys:
  - `9` turns ON LEDs mapped to keys `1..8`
  - `0` turns OFF LEDs mapped to keys `1..8`
  - `*` turns ON LEDs mapped to `A..D`
  - `#` turns OFF LEDs mapped to `A..D`

## Pin Usage Summary
- **Keypad columns**: GP19, GP18, GP17, GP16
- **Keypad rows**: GP26, GP22, GP21, GP20
- **LED outputs**: GP11, GP10, GP9, GP8, GP7, GP6, GP5, GP4, GP3, GP2, GP28, GP27

See full mapping in [docs/wiring.md](docs/wiring.md).

## Running in Wokwi
1. Open a new **Raspberry Pi Pico (Arduino)** project in Wokwi.
2. Copy `src/main.cpp` into the sketch source file.
3. Use `diagram.json` as your hardware definition (replace generated diagram).
4. Ensure the **Keypad** library is available in the project dependencies.
5. Start simulation and press keypad buttons to verify LED responses.

## Running on Real Hardware (Pico W)
1. Wire the keypad and LEDs exactly as in `docs/wiring.md`.
2. In Arduino IDE:
   - Install **Raspberry Pi Pico/RP2040** board support.
   - Select board: **Raspberry Pi Pico W**.
   - Install **Keypad** library.
3. Build and upload the sketch to Pico W over USB.
4. Open Serial Monitor if needed (GP0/GP1 are also routed in the Wokwi design for virtual serial).

## Build Notes
- `CMakeLists.txt` is included to satisfy C/C++ repo structure and documentation requirements.
- The current source is **not** native Pico SDK code. A full Pico SDK build would require porting Arduino calls and keypad handling to SDK equivalents.

## Wi-Fi
This project does **not** use Wi-Fi APIs. No SSID/password configuration is required.

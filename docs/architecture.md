# Firmware Architecture

## Overview
The firmware is a single-module, event-driven sketch:
- `setup()` initializes all LED GPIOs as outputs and drives them LOW.
- `loop()` polls keypad state and executes key-to-action mapping.

## Source Layout
- `src/main.cpp`: complete application logic (preserved from provided code).
- `docs/wiring.md`: electrical and GPIO mapping.
- `docs/architecture.md`: this architecture reference.

## Data Structures
- `keys[4][4]`: keypad character matrix (`1..9`, `0`, `A..D`, `*`, `#`).
- `ledPins[12]`: GPIO list used for LED actuation.
- `rowPins[4]` / `colPins[4]`: keypad scanning pins.
- `Keypad keypad`: matrix scanning object from Keypad library.

## Runtime Flow
1. `keypad.getKey()` returns `NO_KEY` or a pressed character.
2. `switch (key)` dispatches behavior:
   - Single-key LED ON (`1..8`, `A..D`).
   - Group ON/OFF for subsets (`9`,`0`,`*`,`#`).
3. `delay(10)` adds a short poll interval.

## Behavior Guarantees
- Core logic remains unchanged from the provided source.
- LEDs are latched states (remain ON/OFF until another key changes them).
- No Wi-Fi usage, network traffic, or credential handling.

## Potential Future Refactors (non-functional, optional)
- Replace long `switch` with lookup tables for maintainability.
- Abstract LED groups into named helper functions.
- Port to native Pico SDK if Arduino-free toolchain is required.

cmake_minimum_required(VERSION 3.13)
project(pico_w_keypad_led C CXX)

# Note:
# The provided firmware uses Arduino APIs (setup/loop, pinMode, digitalWrite, Keypad library).
# This CMake file exists to provide a clean C/C++ repository structure and documentation anchor.
# Build this project with Arduino-Pico tooling (e.g., Arduino IDE / PlatformIO / Wokwi Arduino mode)
# unless you port the code to native Pico SDK APIs.

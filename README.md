# cec-arduino

Arduino library implementing the HDMI-CEC (Consumer Electronics Control) protocol on a single GPIO pin pair.

> Automatically exported from [code.google.com/p/cec-arduino](https://code.google.com/p/cec-arduino). This is an archived port of the original Google Code project.

## What it does

Provides a layered CEC stack for AVR-class Arduinos:

- `CECWire` — low-level electrical / bit-timing layer that drives the CEC line (read on `IN_LINE`, write on `OUT_LINE`).
- `CEC_LogicalDevice` (`CEC.h`) — protocol state machine handling logical-address allocation and frame send/receive, with device-type enum (`CDT_TV`, `CDT_RECORDING_DEVICE`, `CDT_PLAYBACK_DEVICE`, `CDT_TUNER`, `CDT_AUDIO_SYSTEM`, `CDT_OTHER`).
- `CEC_Device` — concrete device implementation tying the logical layer to the Arduino I/O loop.
- `Common`, `Serial` — shared helpers and a serial debug shim.

The example sketch `CEC_Arduino.pde` instantiates a playback device at physical address `0x1000`, runs in promiscuous mode, and lets you transmit a canned CEC frame (opcode `0x36`, "Standby") in response to the character `1` on the serial port at 115200 baud. Default pins: `IN_LINE = 2`, `OUT_LINE = 3`.

## Stack

- Language: C++ (Arduino)
- Target: AVR Arduino boards
- No external library dependencies

## Build / Run

Copy `Arduino/Lib/CEC_Arduino/` into your Arduino `libraries/` directory, open `CEC_Arduino.pde` in the Arduino IDE, select an AVR board, and upload. Wire CEC's data line to the chosen `IN_LINE` and `OUT_LINE` pins (typically through a level-translation circuit) and connect ground.

## Layout

- `Arduino/Lib/CEC_Arduino/`
  - `CECWire.{h,cpp}` — bit-banged electrical layer
  - `CEC.{h,cpp}` — logical device / protocol state machine
  - `CEC_Device.{h,cpp}` — device implementation
  - `Common.{h,cpp}` — shared helpers
  - `Serial.{h,cpp}` — serial debug helpers
  - `CEC_Arduino.pde` — example sketch

## Status

Archived — Google Code export, no upstream activity.

# ICOM IC-2730 Digital Controller

A custom hardware controller for the ICOM IC-2730 radio, featuring digital audio processing and USB connectivity.

## Overview

This project provides a digital interface for the ICOM IC-2730 radio using a Raspberry Pi RP2350 microcontroller and TLV320AIC3204 audio codec. It handles both transmit and receive audio digitally while managing the radio's unique logic level requirements.

## Hardware
### Main Components

- **Microcontroller: Raspberry Pi RP2350**
  - High processing power
  - Native USB support
  - Familiar development ecosystem

- **Audio Codec: TLV320AIC3204**
  - Integrated DAC and ADC
  - High-quality audio processing

## Key Features
  - USB connectivity for computer interface
  - Bidirectional audio processing (TX/RX)
  - Analog switching circuitry
  - LDO power regulation
  - 3D-printed enclosure with screw mounting

## Design Challenges
**Logic Level Weirdness**
The ICOM IC-2730 uses some very unusual logic levels that I've never encountered before:

- High: 5V
- Low: 3.1V (yes, really!)

**Solution**

- RX path: LM393 comparator to handle the odd voltage levels
- TX path: 5V level shifter (if it reads 3.1V as low, it should read 0V as low too)

**Power Management**
Originally considered a buck converter for efficiency, but went with an LDO since it's perfectly adequate for this application and simpler to implement.

## Notes

- This was my first time using Fusion 360 for CAD work
- Spent way too long figuring out MOSFET power switching
- Enclosure uses screws instead of glue for user serviceability

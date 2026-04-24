# Printrbot Simple Pro — Raspberry Pi + BTT Pico + Klipper + BLTouch Conversion

## Overview
This project documents the process of modernizing a Printrbot Simple Pro by replacing the original control electronics with a Raspberry Pi running Klipper and a BTT SKR Pico control board.

The goal is to transform this legacy printer into a modern, reliable, and highly tunable machine using current open-source firmware and tooling.

---

## Hardware Setup

- Printer: Printrbot Simple Pro (stock frame and motion system)
- Control Board: BigTreeTech SKR Pico
- Host: Raspberry Pi 3B+
- Firmware: Klipper
- Bed Leveling: BLTouch
- Extruder: Stock Printrbot extruder (unchanged)
- Hotend: Stock Printrbot hotend
- Cooling: Stock fans (reconfigured and tuned)

---

## Software Stack

- Klipper (firmware running on Raspberry Pi + Pico)
- OctoPrint (current UI / control interface)
- OrcaSlicer (slicer)
- OctoPi (current OS image)

### Planned Migration

We are currently in the process of migrating from OctoPrint (OctoPi) to a more native Klipper stack:

- Moonraker (Klipper API layer)
- Mainsail or Fluidd (web UI)
- KlipperScreen (touchscreen interface, planned)

## Quick Start

Follow these steps to get the printer up and running with this configuration:

1. Flash Klipper firmware to the BTT SKR Pico
2. Install Klipper on your Raspberry Pi (OctoPi or MainsailOS)
3. Copy `printer.cfg` to your Klipper config directory:
4. Update the MCU serial in `printer.cfg`: Then replace the `serial:` line with your device ID
5. Restart Klipper
6. Home the printer and verify motion
7. Run a test print (e.g., Benchy)

> Note: This configuration assumes a stock Printrbot Simple Pro mechanical setup with upgraded electronics.

---

## Current Project Status

The printer is now:

- Fully operational on Klipper
- Running stable prints without thermal shutdowns
- Using corrected extrusion settings (`rotation_distance`)
- PID tuned for improved thermal response
- Cooling system tuned to prevent heater instability
- Producing successful Benchy prints with good quality

### Recent Major Fixes

- Resolved G2/G3 arc command issues
- Corrected extrusion scaling (`rotation_distance`)
- Tuned cooling behavior to prevent heater shutdown
- Performed PID calibration for stable temperature control

---

## Next Steps

- Final extruder calibration (precise `rotation_distance` measurement)
- Retraction tuning to reduce stringing
- Pressure Advance calibration (Klipper feature)
- Input Shaping for reduced ringing / ghosting
- Migration to Mainsail / Moonraker stack
- Documentation of wiring and full Klipper configuration

---

## Repository Contents (Coming Soon)

All configuration files and documentation will be uploaded shortly, including:

- Klipper `printer.cfg`
- Wiring diagrams for BTT Pico + BLTouch
- Slicer profiles (OrcaSlicer)
- Macros and startup scripts
- Troubleshooting notes and lessons learned

---

## Notes

This project is being actively developed and refined. The current configuration is stable but still undergoing tuning and optimization.

---

## Credits / Inspiration

This project builds on community knowledge of Klipper conversions and Printrbot hardware, with additional tuning and debugging performed during this conversion process.

---

## Contact / Contributions

Feel free to open issues or contribute if you're working on a similar conversion. More documentation will be added as the project evolves.

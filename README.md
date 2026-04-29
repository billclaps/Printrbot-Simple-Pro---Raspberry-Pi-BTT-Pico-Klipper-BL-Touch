# Printrbot Simple Pro — Raspberry Pi + BTT Pico + Klipper + BLTouch Conversion

## Overview
This project documents the modernization of a Printrbot Simple Pro by replacing the original control electronics with a Raspberry Pi running Klipper and a BigTreeTech SKR Pico control board.

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

**Tested with: OrcaSlicer v2.3.2**

### Planned Migration

We are currently migrating to a native Klipper stack:

- Moonraker (Klipper API layer)
- Mainsail or Fluidd (web UI)
- KlipperScreen (touchscreen interface, planned)

---

## Quick Start

Follow these steps to get the printer up and running:

1. Flash Klipper firmware to the BTT SKR Pico
2. Install Klipper on your Raspberry Pi (OctoPi or MainsailOS)
3. Copy `printer.cfg` to: /home/pi/printer_data/config/
4. Update the MCU serial in `printer.cfg`: ls /dev/serial/by-id/
Replace the `serial:` line with your device ID
5. Restart Klipper
6. Home the printer and verify motion
7. Run a test print (e.g., Benchy)

> Note: This configuration assumes a stock Printrbot Simple Pro mechanical setup with upgraded electronics.

---

## Current Project Status

The printer is now:

- Fully operational on Klipper
- Producing stable, repeatable prints
- Thermally stable (no heater shutdowns)
- Mechanically calibrated and dimensionally accurate
- Tuned for clean surface finish and minimal stringing

---

## Final Tuned Configuration

### Print Settings (PLA)

- Nozzle: 0.3 mm  
- Layer Height: 0.2 mm  
- Temperature: 215–220°C  

### Klipper

- Pressure Advance: ~0.11  
- PID tuning completed  

### Retraction

- Distance: 0.8 mm  
- Speed: 35 mm/s  
- Wipe enabled  
- Z-hop disabled  

### Cooling

- Reduced fan speeds (~30–80%) to maintain thermal stability  

### Speed

- ~80 mm/s general print speed  

---

## Tuning Summary

Key improvements achieved during this conversion:

- Corrected extrusion scaling (`rotation_distance`)
- Eliminated heater shutdowns by tuning cooling behavior
- Resolved arc command (G2/G3) compatibility issues
- Applied Pressure Advance to improve corner accuracy and reduce dimensional error
- Tuned retraction and disabled Z-hop to eliminate stringing
- Balanced temperature for optimal flow vs. detail

---

## Next Steps

- Input Shaping for reduced ringing / ghosting
- Migration to Moonraker + Mainsail
- Final documentation of wiring and hardware layout

---

## Repository Contents

This repository will include:

- Klipper `printer.cfg`
- Wiring diagrams (BTT Pico + BLTouch)
- OrcaSlicer configuration bundle (`.orca_printer`)
- Macros and startup scripts
- Troubleshooting notes and lessons learned

---

## Notes

This project has reached a stable and fully functional configuration.  
Further updates will focus on refinement and documentation.

---

## Credits / Inspiration

This project builds on community knowledge of Klipper conversions and Printrbot hardware, with additional tuning and debugging performed during this build.

---

## Contributions

Feel free to open issues or contribute if you're working on a similar conversion.

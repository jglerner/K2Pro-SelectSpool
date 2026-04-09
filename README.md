# K2Pro-SelectSpool

A Klipper macro for the **Creality K2 Pro** that selects which of the four filament spools to use by issuing the corresponding `T0`–`T3` tool change command.

Useful for mono-color prints where you want to pick a specific color spool at the start, or switch color mid-print.

---

## Usage

```gcode
SELECT_SPOOL T=0   ; use spool 0
SELECT_SPOOL T=1   ; use spool 1
SELECT_SPOOL T=2   ; use spool 2
SELECT_SPOOL T=3   ; use spool 3
```

The macro validates the input and raises an error if `T` is outside 0–3.
The active spool is shown on the printer display and logged to the Klipper console.

---

## Installation

1. Copy `select_spool.cfg` into your Klipper config directory
   (`/mnt/UDISK/printer_data/config/` on the K2 Pro).
2. Add to `printer.cfg`:

```ini
[include select_spool.cfg]
```

3. Restart Klipper.

---

## Slicer integration (Orca Slicer)

To select a spool at the start of every print, add a `SELECT_SPOOL` call to your
Machine start G-code before the first layer:

```
SELECT_SPOOL T=0
START_PRINT EXTRUDER_TEMP=[initial_layer_temperature] BED_TEMP=[bed_temperature] ...
```

---

## Compatibility

- Creality K2 Pro with CFS (4-spool filament system)
- Klipper firmware

## License

MIT

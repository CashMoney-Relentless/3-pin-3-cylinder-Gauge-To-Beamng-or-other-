# 3-pin-3-cylinder-Gauge-To-Beamng-or-other-
This is a way to use a 3 pin, 3 cylinder gauge that you might have laying around into something useful for simracing or flightsim

# BeamNG → Processing → Arduino Tach Pack


## Requirements
- BeamNG.drive (with mod support)
- Processing (3.x or 4.x) with Serial library (built-in)
- Arduino IDE
- COM ports as provided: BeamNG -> COM5, Arduino -> COM4


## Installation
1. **BeamNG mod**
- Copy `gaugesController.lua` into your vehicle folder inside the mod (see file tree).
- Add the `luaControllers` snippet to your vehicle's jbeam.
- Repack the mod or keep it in `mods/unpacked`.


2. **Arduino**
- Open `tach_output.ino` in Arduino IDE.
- Upload to your Arduino that appears on `COM4`.
- Ensure `tachPin` is connected to a proper driver and then to your gauge.


3. **Processing**
- Open `BeamNG_to_Arduino_Tach.pde` in Processing.
- If the BeamNG Lua could not open COM5, set `USE_UDP_FALLBACK = true` and configure BeamNG's telemetry UDP to send RPMs to the listener you implement.
- Run the Processing sketch. It will attempt to open COM5 and COM4.


## Troubleshooting
- If BeamNG's `io.open` to COM5 fails, enable `USE_UDP_FALLBACK` and configure BeamNG telemetry to UDP. Then adapt the Processing sketch's UDP section (comment included) to read telemetry.
- If Serial ports fail to open in Processing, try running Processing as Administrator.
- Always use a proper driver for gauge coils; Arduino pins cannot drive them directly.


## Notes
- You can adjust mapping in Processing: `map(rpm, 0, 8000, 5000, 700)` to fit your gauge.
- The pipeline is: BeamNG (COM5) -> Processing -> Arduino (COM4) -> gauge.

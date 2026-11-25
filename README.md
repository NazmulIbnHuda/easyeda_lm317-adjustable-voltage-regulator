# Adjustable LM317 Voltage Regulator

A simple, adjustable linear voltage regulator built around the **LM317**. Feed it a DC input and set the output voltage with a resistor divider. Schematic designed in **EasyEDA**.

## Features

- Adjustable output voltage (about 1.25 V up to roughly 27 V, depending on R2 setting)
- Input and output filter capacitors for stable, low-noise output
- LED power indicator with current-limiting resistor
- Screw-terminal connectors for easy wiring (input and output)
- Compact design, A4 schematic, Version 1.0

## Bill of Materials

| Ref | Component | Value / Part | Description |
|-----|-----------|--------------|-------------|
| U1  | LM317 | – | Adjustable linear regulator |
| R1  | Resistor | 240 Ω | Sets reference current (between OUT and ADJ) |
| R2  | Resistor / trimmer | 5 kΩ | Sets output voltage (between ADJ and GND) |
| R3  | Resistor | 1 kΩ | LED current limiting |
| C1  | Capacitor | 10 µF | Input filter |
| C2  | Capacitor | 10 µF | Output filter |
| D1 / U2 | LED | LTE-4208 | Indicator LED |
| P1  | Connector | KF301-2P | Input terminal (2-pin screw terminal) |
| P2  | Connector | KF301-2P | Output terminal (2-pin screw terminal) |

## How It Works

The LM317 holds a constant 1.25 V reference between its OUT and ADJ pins. R1 and R2 form a voltage divider that sets the output:

```
Vout = 1.25 V × (1 + R2 / R1) + (Iadj × R2)
```

With R1 = 240 Ω and R2 = 0–5 kΩ:

| R2 | Approx. Vout |
|----|--------------|
| 0 Ω | 1.25 V |
| 240 Ω | 2.5 V |
| 720 Ω | 5 V |
| 1.7 kΩ | 10 V |
| 5 kΩ | ~27 V |

(Iadj is about 50 µA, so its effect is small.)

## Usage

1. Connect a DC supply to **P1** (observe polarity).
2. Adjust **R2** to set the desired output voltage.
3. Take the regulated output from **P2**.
4. Verify the output with a multimeter before connecting your load.

## Specifications

| Parameter | Value |
|-----------|-------|
| Input voltage | Vout + 3 V (minimum) up to 37 V max |
| Output voltage | ~1.25 V to ~27 V (adjustable) |
| Max output current | 1.5 A (with proper heatsink) |
| Dropout | ~2–3 V |

## Notes

- **Heatsink:** Power dissipated is `(Vin − Vout) × Iload`. Use a heatsink for higher currents or large voltage drops.
- **Minimum load:** The LM317 needs about 10 mA minimum load for proper regulation; R1 provides this.
- **Input polarity:** Add a protection diode if reverse polarity is possible.
- **Large output capacitors:** Add a protection diode across the regulator if you use large capacitance on the output.

## Files


## Tools

- [EasyEDA](https://easyeda.com) for schematic design

## Version History

- **V1.0** (2026-07-06): Initial release

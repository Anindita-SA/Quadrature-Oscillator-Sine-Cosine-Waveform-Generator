# Quadrature Oscillator - Sine/Cosine Waveform Generator

⚠️ **WORK IN PROGRESS** - Hardware optimization ongoing

## Overview

1kHz quadrature oscillator generating simultaneous sine and cosine waveforms with 90° phase relationship using op-amp integrators.

**Key Specs:**
- Frequency: 1 kHz
- Phase Difference: 90° (quadrature)
- Output: ~2.4V peak
- Supply: ±15V
- IC: LM358 dual op-amp

## Circuit Design
![alt text]([https://github.com/Anindita-SA/Quadrature-Oscillator-Sine-Cosine-Waveform-Generator/blob/main/Final%20PCB%20for%201khz%20Sine%20wave%20generator%201.png])
### Topology
State-variable quadrature oscillator implementing:
```
d(sine)/dt = ω × cosine
d(cosine)/dt = -ω × sine
```

### Schematic
![Circuit Schematic](path/to/schematic.png)

### Components

| Component | Value | Function |
|-----------|-------|----------|
| R1, R2, R3, R4 | 1.6kΩ | Frequency setting |
| C1, C2, C3 | 100nF | Integrator capacitors |
| R5, R7 | 1kΩ | Bias network |
| R6, R10 | 8kΩ | Voltage divider |
| D1, D2 | 1N4148 | Amplitude limiting |
| U1, U2 | LM358 | Op-amps (2 ICs) |

## Calculations

**Frequency:**
```
f = 1/(2πRC) = 1/(2π × 1.6kΩ × 100nF) ≈ 995 Hz
Measured: 1.01 kHz (±1%)
```

**Output Amplitude:**
```
V_bias = 15V × 1kΩ/9kΩ = 1.67V
V_peak = V_bias + V_diode = 1.67V + 0.7V = 2.37V
Measured: ~2.4V ✓
```

**Phase:**
```
Target: 90°
Measured: 83-85° (within tolerance)
```

## Performance

| Parameter | Target | Simulation | Hardware |
|-----------|--------|------------|----------|
| Frequency | 1000 Hz | 1009 Hz | 1030 Hz |
| Phase | 90° | 91.7° | 83-85° |
| Amplitude | ~5V pp | 4.68V pp | ~2.4V |

## Design Evolution

1. **Wien Bridge** → Abandoned (complex amplitude control)
2. **All-Pass Filter** → Abandoned (wrong phase shift)
3. **Quadrature Oscillator** → Current (functional, optimizing)

## Known Issues

- **Hardware distortion** - LM358 slew rate limiting + breadboard parasitics
- **Phase accuracy** - Component tolerances cause 5-7° deviation
- **Amplitude variation** - Working on stabilization

## To-Do

- [ ] PCB implementation
- [ ] Add frequency adjustment potentiometer

## Files

- `schematic.png` - Circuit diagram
- `simulation.asc` - LTspice file
- `calculations.md` - Design math
- `troubleshooting.md` - Issues log

## Build Notes

**Critical:**
- Use **film capacitors** for C1, C2, C3 (not ceramic)
- Verify component markings ("103" = 10nF, "104" = 100nF)
- Add 0.1µF decoupling caps close to IC pins
- Keep wires short on breadboard

## References

- Horowitz & Hill, "Art of Electronics" (3rd Ed., §5.17)
- [YouTube reference video](link)

## License

Educational/open source - standard quadrature oscillator topology

## Contact

[Your links]

**Status:** Active development - contributions welcome

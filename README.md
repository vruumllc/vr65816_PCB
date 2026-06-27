# vr65816
65816 Single Board Computer compatible with Rumbledethump's Picocomputer Architecture

## Goals

- Uses 2 RasberryPi Pico2s with firmware derived from Rumbledethumps' rp6502
- 65816 runs at 1 kHz to 8Mhz, clocked by Pico2 RIA
- Prototyped on a breadboard, through-hole ICs only, no programmable logic
- No ROM, 1MB RAM, 64KB extended RAM
- 65C22 for timers and peripheral I/O
- Runs all existing applications for the Rumbledethumps' RP6502 Picocomputer

## Timing diagrams

### Clock

<details><summary>View source</summary><p>

```js
{
  signal: [
    { name: 'CLK_SRC', wave: '0..(25)x(10)1(40)x(10)0(17)', phase: 0.20 },
    { nodes: ['...(25)Ο(5)Ό(5)G(40)H(5)R(5)P', '...(30)Ν(10)Ά(40)Β(10)Ξ'], phase: 0.45 },
    { name: 'CLK-', wave: '0..(37.5)x(5)1(45)x(5)0..(7.5)', phase: 0.20 },
    { nodes: ['...(37.5)Ё(2.5)Ж(2.5)S(45)T(2.5)Ћ(2.5)Δ', '...(40)L(10)K(40)M(10)Σ'], phase: 0.45 },
    { name: 'CLK', wave: '1.0(50)1(50)0.', phase: 0.20 },
    { nodes: ['..Θ(10)Λ(40)Њ(10)Ќ', '...(7.5)Љ(2.5)Є(2.5)Υ(45)Ю(2.5)Ψ(2.5)Ω'], phase: 0.45 },
    { name: 'CLK+', wave: '1..(7.5)x(5)0(45)x(5)1..(37.5)', phase: 0.20 },
    {},
    { nodes: ['..Ε(8.5)Ι(41.5)Κ(8.5)Μ', '..Ρ(1)Τ(49)Χ(1)А'], phase: 0.45 },
    { name: '~CLK', wave: '0..(1)x(7.5)1(42.5)x(7.5)0..(41.5)', phase: 0.20 },
  ],
  edge: [
    'Ν+Ά 10ns', 'Β+Ξ 10ns', 'Ο+Ό 5ns', 'Ό+G 5ns', 'H+R 5ns', 'R+P 5ns',
    'L+K 10ns', 'M+Σ 10ns', 'Ё+Ж 2.5ns', 'Ж+S 2.5ns', 'T+Ћ 2.5ns', 'Ћ+Δ 2.5ns',
    'Θ+Λ 10ns', 'Њ+Ќ 10ns', 'Љ+Є 2.5ns', 'Є+Υ 2.5ns', 'Ю+Ψ 2.5ns', 'Ψ+Ω 2.5ns',
    'Ε+Ι 8.5ns', 'Κ+Μ 8.5ns', 'Ρ+Τ 1ns', 'Χ+А 1ns'
  ],
  config: {
    skin: 'narrower',
    lines: {
      offset: 2,
      every: 50
    },
    background: 'white',
  },
  head: {
    tick: -2,
    every: 10,
    text: ['tspan', { "font-size": '12px' }, 'based on 10Mhz clock']
  }
}
```
</p></details>

[![Clock](./timing/Timing%20Clock.png)](./timing/Timing%20Clock.png)


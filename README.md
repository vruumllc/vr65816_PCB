# vr65816
WDC 65C816 Single Board Computer compatible with [Rumbledethump's Picocomputer Architecture](https://picocomputer.github.io/)

## Goals
- Use 2 [RasberryPi Pico2s](https://www.raspberrypi.com/products/raspberry-pi-pico-2/) with [Rumbledethumps' rp6502 firmware](https://github.com/picocomputer/rp6502)
- Run [WDC 65C816](https://www.westerndesigncenter.com/wdc/documentation/w65c816s.pdf) at up to 8Mhz, clocked by Pico2W RIA
- Use currently produced through-hole ICs only, and no programmable logic
- Use 1MB SRAM, 64kB extended RAM (on Pico2W RIA), and no hardware ROM
- Use [WDC 65C22](https://www.westerndesigncenter.com/wdc/documentation/w65c22s.pdf) for timers and peripheral I/O
- Use [KiCad](https://www.kicad.org/download) to create fully open source schematic and board source files
- Run all existing apps and games ("ROMs") for the Rumbledethumps' RP6502 Picocomputer
- Enable [creation](https://github.com/picocomputer/rp6502-sdk) of new "ROMs" utilizing [advanced features and memory of the '816](https://archive.org/details/0893037893ProgrammingThe65816/mode/2up) 


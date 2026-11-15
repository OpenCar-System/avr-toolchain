# AVR-Toolchain für PlatformIO – OpenCar-System

Gemeinsame AVR-GCC-Toolchain für alle OpenCar-Firmware-Projekte, als PlatformIO-Paket.
Die Pakete liegen als Anhänge an den [Releases](../../releases).

## v14.1.0

| Komponente | Version |
|---|---|
| AVR-GCC | 14.1.0 |
| AVR-Binutils | 2.42 |
| AVR-LibC | 2.2.0 |
| System | Linux x86_64 |

Verwendung in `platformio.ini`:

```ini
[env]
platform = atmelavr
platform_packages = toolchain-atmelavr@https://github.com/OpenCar-System/avr-toolchain/releases/download/v14.1.0/toolchain-atmelavr-14.1.0-linux-x64.tar.gz
```

PlatformIO lädt das Paket einmal nach `~/.platformio/packages/`; alle Projekte mit derselben URL nutzen es gemeinsam.

### Herkunft

Unveränderter Build von Zak Kemble, Release
[v14.1.0-1](https://github.com/ZakKemble/avr-gcc-build/releases/tag/v14.1.0-1)
(`avr-gcc-14.1.0-x64-linux.tar.bz2`, SHA256 `4e9c6edf520765cdefa2d9af3304681296de24c3e095750e3be5504c12d3b224`).

Geändert: GDB und Simulator entfernt (`avr-gdb`, `avr-gdb-add-index`, `avr-run`, `libavr-sim.a`,
`include/gdb`, `include/sim`, `share/gdb`, `gdb.info`), `package.json` und `LIESMICH.txt` ergänzt.

### Hinweise zu avr-libc 2.2

- ATmega328PB: SPI-Bitnamen ohne Endziffer (`SPE`, `SPIF`, … statt `SPE0`, `SPIF0`, …).
- GCC ≥ 10 verwendet `-fno-common`: Variablen im Header nur `extern` deklarieren.

### Lizenzen

GCC und Binutils: GPL v3 (libgcc mit GCC Runtime Library Exception – die erzeugte Firmware
unterliegt dadurch keinen zusätzlichen Bedingungen). AVR-LibC: BSD-artig. GMP, MPFR, MPC: LGPL. ISL: MIT.

Die vollständigen Quelltexte (gcc, binutils, avr-libc, gmp, mpfr, mpc, isl, gettext) und das
Build-Skript `avr-gcc-build.sh` liegen als Anhänge im selben Release. Prüfsummen: `SHA256SUMS`.

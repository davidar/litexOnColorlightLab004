# litexOnColorlightLab004

Demonstration on using a Soft Core (**VexRiscv**)
built with **LiteX** on a **Colorlight i5/i9** (ECP5).

## Prerequisite

### software

- [OSS CAD Suite](https://github.com/YosysHQ/oss-cad-suite-build)
- [LiteX](https://github.com/enjoy-digital/litex)
- remember to [setup udev rules](https://github.com/adamgreig/ecpdap/tree/master/drivers)

If using WSL2:
- [usbipd](https://github.com/dorssel/usbipd-win)
- [kernel with `CONFIG_USB_HIDDEV` enabled](https://github.com/microsoft/WSL2-Linux-Kernel/releases/tag/linux-msft-wsl-5.15.150.1)

## Build

### gateware

```sh
python3 -m litex_boards.targets.colorlight_i5 --board i9 --revision 7.2 --cpu-type vexriscv --build --load --ecppack-compress
```

### firmware

```sh
make -C firmware
```

## load firmware

```sh
litex_term --kernel firmware/firmware.bin /dev/ttyACM0
```

If you started the terminal too late to see the LiteX BIOS, type `reboot` to restart the CPU.

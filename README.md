# GameCube controller picowalker

## About

The overall Picowalker project is to make a cool kinda of debugger/ walker GameCube controller. I have a few ideas for how I want this project to feel. 
This includes the features in the base project, and a few extra things like the steps being counted via button presses, and potentially a screen for a gcc phob.

I take no credit for the work that has gine into this, please check the links.
See the core code for this project: [picowalker-core](https://github.com/mamba2410/picowalker-core).

See the custom hardware these drivers are for: [picowalker-hardware](https://github.com/mamba2410/picowalker-hardware)



- `hardware-v0.1` - The current active branch, drivers specific to the 
    [custom PCB](https://github.com/mamba2410/picowalker-hardware) used as a
    stepping stone to creating a modern rebuild.

## Project state

This is working with the [picowalker-hardware v0.1](https://github.com/mamba2410/picowalker-hardware)
which is a Raspberry Pi Pico 2 based custom PCB, including:

- DO180PFST05 OLED screen controlled over PIO QSPI or the rp2350 HSTX (SH8601Z driver)
    - On-the-fly decode of picowalker images to RGB565.
    - Currently only greyscale images.
- IrDA over PIO via Dmitry Gr.
    - Currently CPU-fed but needs to be DMA-fed
- M95512 64kB EEPROM
- Step detection, via button inputs.
- powered by the GameCube controller, while plugged in.
- Debugging on swd
- Generic push buttons
- USB (TinyUSB)
    - Mass Storage Controller (MSC) for backing up and restoring the eeprom save data.
- RTC
    - Using RP2350's AON timer (internal LPOSC)

Hardware to get working:
    - Safe shutdown when un plugged
- Sound trayed as rumble
- Colour sprites.

## Building and Testing

You can follow the detailed [tutorial](docs/TUTORIAL.md).
I will update the process to incorporate this into a GameCube controller.

### Debugging with The Raspberry Pi Debug Probe and openocd

Make sure you get Raspberry Pi's [openocd build](https://github.com/raspberrypi/openocd) and follow the build instructions in [Appendix A of the getting started guide](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf).

I'm also using the Raspberry Pi debug probe which is a really easy and cheap (~$15) USB debug adapter for ARM devices.

## Resources

### Pico

- [Pico SDK](https://github.com/raspberrypi/pico-sdk)
- [Getting Started with Pico C](https://www.raspberrypi.org/documentation/rp2040/getting-started/#getting-started-with-c)
- [Pico 2 Datasheet](https://datasheets.raspberrypi.com/pico/pico-2-datasheet.pdf)
- [RP2350 Datasheet](https://datasheets.raspberrypi.com/rp2350/rp2350-datasheet.pdf)

### Pokewalker

- [Original pokewalker hack by Dmitry.GR](http://dmitry.gr/?r=05.Projects&proj=28.%20pokewalker)
- [H8/300h Series software manual (for reverse-engineering)](https://www.renesas.com/us/en/document/mah/h8300h-series-software-manual)

### Hardware

(datasheets for the hardware go here when we have them)
See [design doc for now](docs/DESIGN.md)

## License

Either MIT or GPL-3, whichever you want.

If you fork or make changes, I'd love to know what cool things you're doing with it!

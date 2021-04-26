# Bootloader

## If you buy a kit from cftkb.com your microcontroller already has the bootloader flashed and you do not need this

This project uses USBaspLoader as the usb bootloader on the atmega32a.

- My [custom bootloader](https://github.com/dcorbeil/USBaspLoader):
  - Please ensure you are in the atmega32a branch of my fork of the USBaspLoader repository when downloading.
  - Follow the directions in the readme for directions on setting up the build environment for your operating system as well as flash instructions.
    - In short (Debian/Ubuntu): install the `avr` cross compiler:

      ```shell
      sudo apt-get install gcc-avr binutils-avr gdb-avr avr-libc avrdude
      ```

  - `Makefile.inc` sets flashing device as usbtiny, as I use a Sparkfun Pocket AVR Programmer ([Amazon](https://www.amazon.com/dp/B004G54E9I?psc=1&smid=AM0JQO74J587C&ref_=chk_typ_imgToDp)) ([Sparkfun](https://www.sparkfun.com/products/9825)). If you need to use another programmer please edit line 41 of Makefile.inc accordingly. Only edit `Makefile.inc`, and NEVER directly edit the actual `Makefile`.

  - Wire in the Sparkfun Pocket AVR Programmer (TODO: Add info here)
  - Commands for flashing once build environment is set up:
    - Flashes the bootloader:

    ```shell
    make flash
    ```

    - Sets fuse bytes for microcontroller. Fuse bytes are basically configuration bytes. [More info](http://playwithrobots.com/avr-fuse-bits/#:~:text=ATmega32%20microcontroller%20has%20two%20fuse,0x99%20and%20low%20fuse%20%3D0xE1.) on the ATmega32:

    ```shell
    make fuse
    ```

  - The bootloader is now flashed!

## Enter bootloader mode

1. Press and hold ```BOOT``` switch
2. Tap ```RESET``` switch
3. Release ```BOOT``` switch

Alternatively, you can hold ```BOOT``` switch while inserting the USB cable.

If you have successfully entered bootloader mode you should see USBaspLoader in device manager or as a connected device in QMK Toolbox.

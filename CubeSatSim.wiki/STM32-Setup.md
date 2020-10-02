Instructions from https://siliconjunction.wordpress.com/2017/03/21/flashing-the-stm32f-board-using-a-raspberry-pi-3/ specifically for the STM32F103C8T6 "blue pill" Mini Maya Arduino compatible board.

First install software on a Raspberry Pi, wire STM32 up to Pi, flash bootloader onto STM32, then unplug from Pi, install software and drivers on PC, then plug micro USB cable into PC and test programming using Blink program.

### Preparing the Raspberry Pi

Install the stm32flash utility:

`git clone https://git.code.sf.net/p/stm32flash/code stm32flash-code`

`cd stm32flash-code`

`sudo make install`

Move the high performance UART from the Bluetooth device to  the GPIO pins:

`sudo nano /boot/config.txt`

Add the following line:

`dtoverlay=pi3-miniuart-bt`

Edit cmdline.txt:

`sudo nano /boot/cmdline.txt`

Remove the following text in cmdline.txt to prevent a console from running on the serial port:

`console=serial0,115200`

You should now wire up your micro-controller to the Pi as follows:

`Raspberry Pi 3.3V (pin 1) to STM32 3.3V`

`Raspberry Pi GND (pin 6) to STM32 GND`

`Raspberry Pi TX (pin 8) to STM32 RX (pin PA10)`

`Raspberry Pi RX (pin 10) to STM32 TX (pin PA9)`

STM32 Pinout https://circuitdigest.com/sites/default/files/inlineimages/u/STM32-Pin-Details_0.png
Raspberry Pi Pinout https://pinout.xyz/

Set the STM32 BOOT0 jumper to 1 (away from micro USB connector)

### Flashing a boot-loader

If you want to use the Arduino IDE  you can use the image below, alternatively you could flash your own compiled binary directly to the micro-controller.

`wget https://github.com/rogerclarkmelbourne/STM32duino-bootloader/raw/master/binaries/generic_boot20_pc13.bin`

Press the RESET button on your micro controller before running stm32flash

`stm32flash -v -w ./generic_boot20_pc13.bin /dev/serial0`

Restore the jumpers to their original configuration (jumper close to micro USB connector)

### Arduino Programming IDE

To use the Arduino IDE to program the STM32; plug the STM32 into a usb port follow the STM32duino installation instructions here:

https://github.com/rogerclarkmelbourne/Arduino_STM32/wiki/Installation

Set board and port to Maple Mini

Open Examples/A_STM32_Examples/Digital/Blink and edit LED pin to PC13 and compile!
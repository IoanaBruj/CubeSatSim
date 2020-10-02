The PCB has components on both sides. This is the top of the PCB, with the AMSAT logo.

![Step 1](https://countingfromzero.net/amsat/new/1.JPG)

This is the bottom of the PCB.

![Step 2](https://countingfromzero.net/amsat/new/2.JPG)

The silkscreen markings indicating which side to mount the parts.    The exception is the three LEDs which are marked on the top side but should be mounted on the bottom side.

Before any components are soldered onto the board, the Surface Mound Device (SMD) components for the Band Pass Filter (BPF) must be soldered, if they aren't already soldered on. Here's the board with the SMD components:

![Step 3](https://countingfromzero.net/amsat/new/3.JPG)

The first step is the solder the resistors onto the top of the PCB, as shown here.

![Step 4](https://countingfromzero.net/amsat/new/4.JPG)

Note that R5, R7, and R9 should be left unconnected.  Next, the micro USB connector, RBF switch, pushbutton switch, and three LEDs should be soldered on the bottom of the PCB.  The micro USB board is first soldered to the 1x5 pin header that came with the board.  One way to easily solder this straight is to use the STEM Payload board along with a 1x6 pin header from one of the INA219 boards as shown here:

![Step 5](https://countingfromzero.net/amsat/new/5.JPG)

Solder the 1x5 pin header as shown:

![Step 6](https://countingfromzero.net/amsat/new/6.JPG)

Next, trim the excess length of the 1x5 pin headers

![Step 7](https://countingfromzero.net/amsat/new/7.JPG)

Then, solder the RBF switch (3.5mm audio jack), push button switch, micro USB header, and the three LEDs.  The longer leg on the LED is usually the '+' and should be away from the edge of the PCB:

![Step 8](https://countingfromzero.net/amsat/new/8.JPG)

Next, solder the stacking GPIO header.  The female side of the connector should be on the bottom of the PCB.  The pins are soldered on the top PCB:

![Step 9](https://countingfromzero.net/amsat/new/9.JPG)

Next, solder the 1x6 pin headers on four of the INA219 boards, using the same approach as for the micro USB board:

![Step 10](https://countingfromzero.net/amsat/new/10.JPG)

Trim the excess pin header leads.  Then, set the I2C addresses to all four combinations of solder bridges on the A0 and A1 bridge pads.  This will give four I2C addresses: 0x40 (no bridges), 0x41 (A0 bridge only), 0x44 (A1 bridge only), and 0x45 (A0 and A1 bridges) as shown:

![Step 11](https://countingfromzero.net/amsat/new/11.JPG)

The four INA219 boards should be soldered onto the bottom of the PCB - the correct address for each one is labeled on the PCB, which are, clockwise from the top right, 0x45, 0x40, 0x41, and 0x44.

![Step 12](https://countingfromzero.net/amsat/new/12.JPG)

This completes the bottom of the PCB.  The top of the PCB will look like this:

![Step 13](https://countingfromzero.net/amsat/new/13.JPG)

Next, solder the 7 1N517 diodes.  Pay attention to the polarity, as shown in this closeup of the three diodes D5, D12, and D13, showing how to mount them so they do not get in the way of the -Y INA219 board:

![Step 14](https://countingfromzero.net/amsat/new/14.JPG)

With all the diodes soldered in:

![Step 15](https://countingfromzero.net/amsat/new/15.JPG)

Next, solder the 8 JST 2.0 connectors, the PTC, and the zener diode, as shown:

![Step 16](https://countingfromzero.net/amsat/new/16.JPG)

Then, prepare four more INA219s, setting the four possible addresses as before.  Solder them in, paying attention to the labels on the PCB, which is from top right going clockwise: 0x45, 0x44, 0x41, and 0x40:

![Step 17](https://countingfromzero.net/amsat/new/17.JPG)

Cut 8 individual pin headers, and insert in the board (do not solder yet) for the 5V boost converter board and NiMH charger board as shown:

![Step 18](https://countingfromzero.net/amsat/new/18.JPG)

Then, place the 5V boost converter board and NiMH charger board on the pins:

![Step 19](https://countingfromzero.net/amsat/new/19.JPG)

Solder the top of the pins:

![Step 20](https://countingfromzero.net/amsat/new/20.JPG)

Then solder the bottom of the pins.  The bottom of the PCB should look like this:

![Step 21](https://countingfromzero.net/amsat/new/21.JPG)

And the top should look like this:

![Step 22](https://countingfromzero.net/amsat/new/22.JPG)

The main PCB is now complete!












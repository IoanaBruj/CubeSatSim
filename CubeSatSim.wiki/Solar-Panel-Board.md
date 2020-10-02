## Important Note: this archived page is for the CubeSat Simulator Solar Power Board version vB1.

If you are a Beta builder who is using the first generation beta board, vB1, then follow these instructions.  Otherwise, follow the instructions on [Solar Power Board](Solar-Power-Board)

Back to the [CubeSat Simulator Wiki Home](Home).

### Schematic:

![CubeSat Simulator Solar Panel Board Schematic](https://raw.githubusercontent.com/alanbjohnston/CubeSatSim/master/kicad/cubesatsim_solar_board.png)

## Building Information:

KiCad files [https://github.com/alanbjohnston/CubeSatSim/tree/master/kicad](https://github.com/alanbjohnston/CubeSatSim/tree/master/kicad)

Here is the PCB Design

![PCB Layout](https://raw.githubusercontent.com/alanbjohnston/CubeSatSim/master/kicad/PCB.png)

![PCB Front](https://countingfromzero.net/amsat/PCB_front.jpg)
![PCB Front](https://countingfromzero.net/amsat/PCB_back.jpg)

### Assembly of PCB Instructions:

Materials:

* 1x AMSAT CubeSat Simulator Solar Power Board PCB
* 1x 40 pin extra long (19mm) male breakaway headers, straight 
* 1x 40 pin regular length male breakaway headers, straight
* 2x 40 pin regular length female headers
* 1x 40 pin right angle male breakaway headers
* 1x Boost module 
* 5x diodes, 1N5817
* 2x resistors 4.7k Ohm, 1/4 watt
* 6x INA219 Sensor boards


![PCB Front](https://countingfromzero.net/amsat/PCB_parts.jpg)

Steps:

1. Break 40 pin extra long male breakaway header into two 20 pin headers, and use for GPIO connector.  Solder into place, being careful that the two rows are parallel and at right angle to the board (A 2x20 pin stackable header could be inserted into them a short way to ensure this).  After it cools, test plugging Pi Zero W board with stackable header into the PCB. Note: not every pin needs to be soldered: required pins: 1,2,3,4,5,6,9,14,20,25,27,28,30,34,39.

![PCB with GPIO header installed](https://countingfromzero.net/amsat/steps/0.jpg)

2. Break 40 pin regular length male breakaway header into 1x 12 pin (A combined J1 and J2 connector), 2x 2 pin (J3, J4), and 1x 5 pin (J5). Solder J1/J2, and J3, J4, and J5 into board.

![PCB with J1 - J5 installed](https://countingfromzero.net/amsat/steps/3.jpg)

3. Solder resistors R1 and R2 vertically.

![PCB with R1 and R2 installed](https://countingfromzero.net/amsat/steps/4.jpg)

4. Break off 4 single pins from the regular length male breakaway header and solder into the four terminals of the PCB U1 for the Boost Converter Module for IN+, IN-, OUT+, and OUT-.  

![PCB with U1 headers installed](https://countingfromzero.net/amsat/steps/5.jpg)

Mount Boost Converter Module U1 onto the pins and solder in place.

![PCB with Boost Converter installed](https://countingfromzero.net/amsat/steps/6.jpg)

5. Solder diodes D1, D2, D3, D4, and D5 vertically.  Cathode (marked by a band on diode package) goes into the square hole (on left), while the Anode goes into the round hole (on right). Note: some solar panels have a built in diode, in which case the diode can be replaced with a jumper wire.

![PCB with Diodes installed](https://countingfromzero.net/amsat/steps/1.jpg)
![PCB with Diodes Closeup](https://countingfromzero.net/amsat/steps/7.jpg)

6. Cut 90 degree breakaway headers into 6x 6 pin lengths.  

![PCB with 90 Degree Headers](https://countingfromzero.net/amsat/steps/8.jpg)

7. Set the correct I2C bus address on the 6x INA219 boards by adding solder to jumpers to bridge A0 and A1 as needed.  See instructions at https://learn.adafruit.com/adafruit-ina219-current-sensor-breakout/assembly (Note: do not use the pins and connectors that came with the INA219 board).  Set the jumpers using this list:
* J7 X+ Board: Bus /dev/i2c-1 Address = 0x40 Offset = binary 00000 (no jumpers required)
* J8 Y+ Board: Bus /dev/i2c-1 Address = 0x41 Offset = binary 00001 (bridge A0)
* J9 Z+ Board: Bus /dev/i2c-1 Address = 0x44 Offset = binary 00100 (bridge A1)
* J10 Vbatt Board: Bus /dev/i2c-1 Address = 0x45 Offset = binary 00101 (bridge A0 and A1)
* J11 X- Board: Bus /dev/i2c-0 Address = 0x40 Offset = binary 00000 (no jumpers required)
* J12 Y- Board: Bus /dev/i2c-0 Address = 0x41 Offset = binary 00001 (bridge A0)

8. Solder the 6 pin 90 degree headers into the boards so the pins face downward.

![PCB with Diodes Closeup](https://countingfromzero.net/amsat/steps/9.jpg)

9. Cut two 40 pin female headers into 1x 5 pin (J6), 6x 6 pin (J7, J8, J9, J10, J11, J12).  See https://www.instructables.com/id/How-to-cut-pin-headers/ for good tips on how to sacrifice one pin to ensure the cut header has full stregth. 

![PCB with Female Headers](https://countingfromzero.net/amsat/steps/10.jpg)

Solder J7-J12 onto the board.

![PCB with J7-J12](https://countingfromzero.net/amsat/steps/11.jpg)

10. Test fit the INA219 boards vertically into connectors J7 through J12, but do not leave them plugged in.

![PCB with Sensor Boards](https://countingfromzero.net/amsat/steps/12.jpg)
![PCB with Sensor Boards](https://countingfromzero.net/amsat/steps/13.jpg)

### Remove Before Flight (RBF) Switch

Materials:

* 1x 3.5mm TRS female audio jack with 2 switches
* 1x 3.5mm TRS male plug
* 5x female jumper wires (keep attached together if possible)
* 1x Remove Before Flight keyring

![RBF Materials](https://countingfromzero.net/amsat/steps/18.jpg)

Steps:

1. Plug female ends of jumper wires into J5 connector and measure length for position of RBF switch. Cut to length and trim wires
2. Solder onto 3.5mm audio jack per schematic
3. Remove screw cover on male TRS plug and drill hole through for mounting RBF tag or other handle
4. From jumper wire remains, cut a jumper wire short enough to stay inside the cover of the male jack to connect pins 3 and 1 (center to outer conductors). Solder jumper wire and put cover back on
5. Attach Remove Before Flight keyring through the hole in the cover, taking care not to hit the jumper or connector.

![PCB with Diodes Closeup](https://countingfromzero.net/amsat/steps/19.jpg)

6. Test switch while unplugged from PCB using DMM set to Ohms or continuity:
* With the plug in, there is a short circuit between pins 4 and 5.  There is an open circuit between pins 1 and 2, and pins 3 and 4.
* With the plug out, there is a short circuit between pins 1 and 2, and between pins 3 and 4. There is an open circuit between pins 4 and 5.

7. Mount switch on CubeSat frame on top but do not plug into J5 yet.


### DC Charging Cable

Materials:

* 1x Barrel power connector 5.5mm x 2.1mm female
* 2x Female jumper wires

Steps:

1. Plug female jumper wires into connector J3.  Measure and cut length based on barrel connector mount position on frame
2. Solder wires to connector.
3. Connect center of barrel connector to J3 pin 1.  Connect outer conductor of barrel connector to J3 pin 2.  Leave unplugged.

![PCB with Charging Cable](https://countingfromzero.net/amsat/steps/23.jpg)


### Battery Monitoring Cable

Materials:

* 2x 9V snap connector wires
* 1x female to female jumper 

![Battery Cable Parts](https://countingfromzero.net/amsat/steps/16.jpg)

Steps:

1. Cut jumper wire in half. Solder one half of the jumper wire to a positive lead of one 9V connector (red lead) and solder the other half to the negative  lead of the other 9V connector (black lead)
2. Solder the other ends of the two 9V connectors together (black to red leads).

![PCB with Battery Cable](https://countingfromzero.net/amsat/steps/17.jpg)

3. Plug jumper wire into J2 with the positive lead of the connector into pin 1, and the negative lead of the connector plugged into pin 2 of J2.
4. Plug the NiMH battery into the connector that the positive lead is wired to the header connector.  Plug the connector from the MoPower UPS V2 board into the other connector. CHECK!
5. Verify Pi boots and runs from the battery.

### Solar Panels

Materials:

* 6x solar panels
* 12x female to female jumper wires
* 1x mounting square, foam

Steps:

1. Cut off one end of each of the female to female jumper wires.  Solder two to each solar panel, using a different color for the positive (+) and negative (-) connections.
2. Cut mounting square into small squares, and use one each corner to mount solar panels on the frame of the CubeSat Simulator.  You may need to drill holes for the wires to go through.

### Vin to MoPower Cable

Materials:

* 1x red female to female jumper wire
* 1x black female to female jumper wire

Steps:

1. Plug red female to female jumper wire into J4 pin 1
2. Plug black female to female jumper wire into J4 pin 2

## Putting it all together and Testing

1. Plug Pi Zero W board into this board. Power up Pi and make sure Pi works fine.  Check J6 for 3.3V (pin 2 to pin 3) and 5V supply (pin 1 to pin 3). On J7-J12, check pins 6 to 5 for 3.3V. Shutdown the Pi.

2. Plug in INA219 boards to J7 - J12 and power up the Pi. Run `i2cdetect -y 1` command on Pi. You should see each INA219 Board you have plugged in (40, 41, and 44, and 45 for J7, J8, J9, and J10):

 `. . 00 01 02 03 04 05 06 07 08 09 0a 0b 0c 0d 0e 0f`

`00:          -- -- -- -- -- -- -- -- -- -- -- -- -- `

`10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- `

`20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- `

`30: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- `

`40: 40 41 -- -- 44 45 -- -- -- -- 4a -- -- -- -- -- `

`50: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- `

`60: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- `

`70: -- -- -- -- -- -- -- -- ` 

 (If you have the Current Sensor module included in the MoPower UPS V2 board, you will also see it at 4a as well). If not, check A0 and A1 jumpers and soldering of the missing board.  If `i2cdetect -y 1` returns all dashes, did you bend two of the GPIO connector pins (pins 3 and 5) on the MoPower UPS board so that when you plug the Digital Transceiver board into it, they do not make contact? Run `i2cdetect -y 0` command on Pi. 

 `. . 00 01 02 03 04 05 06 07 08 09 0a 0b 0c 0d 0e 0f`

`00:          -- -- -- -- -- -- -- -- -- -- -- -- -- `

`10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- `

`20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- `

`30: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- `

`40: 40 41 -- -- -- -- -- -- -- -- -- -- -- -- -- -- `

`50: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- `

`60: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- `

`70: -- -- -- -- -- -- -- -- ` 

You should see the other INA219 Board you have plugged in (40 and 41 for J11 and J12).  If not, check A0 and A1 jumpers and soldering of the missing board.

3. Run the Sensor only software on the Pi:

`python ~/CubeSatSim/python/telem.py`

You should see results for all the boards. Plug in an illuminated solar panel into J1 for X+ (pin 1 to + and pin 2 to -) and rerun the Sensor only software - you should see the X+ voltage (open circuit voltage of the solar panel), and current (approximately zero) and power (approximately zero). Repeat for Y+, Z+, X-, and Y- (if you have them) (pins 3 and 4, pins 5 and 6, pins 7 and 8, and pins 9 and 10). For example, with just one solar panel plugged in, you might see:

`X+ (0x40) v= 3.772 V i= -0.0914634146341 mA p= 0.0 mW`

`Y+ (0x41) v= 1.32 V i= -0.0914634146341 mA p= 0.0 mW`
 
`Z+ (0x44) v= 1.3 V i= 0.0 mA p= 0.0 mW`
 
`X- (0x45) v= 0 V i= 0 mA p= 0 mW`
 
`5V Supply(0x4a) v= 5.088 V i= 200.0 mA p= 849.085365854 mW` 

4. Illuminate at least one solar panel (if you are using a halogen light, be careful not to get it too hot - keep a safe distance between the lamp and the Simulator). Plug a connector wire into J4 and measure the voltage, red to black (pins 
1 to 2). With the RBF pin in, you should measure 0V. Remove the RBF pin and this should jump to around 30V.  Shutdown the Pi (by pressing and holding the button on the MoPower board for 3 seconds, or by typing `sudo shutdown now`. Unplug the solar board from the rest of the board stack by unplugging the GPIO connector.

5. With the Pi not plugged in, you can adjust the trimpot using a jewelers screwdriver or trimpot adjuster on the boost converter U1 so that the voltage on J4 pins 1 to 2 reads around 15V when at least one solar panel is in full illumination. Turning clockwise will reduce the output voltage. It may take approximately 3 turns. Put the RBF pin back in, and the voltage on J4 pins 1 to 2 should drop to zero.

6. With the RBF pin plugged in, plug in the DC in barrel power cable into J3.  With a DC power pack plugged in, you should read around 15V on J4 pin 1 to 2.  

7. On the MoPower UPS V2 board, solder a male connector cable into the Vin2 + (red) and - (black) holes.   


![MoPower Cable](https://countingfromzero.net/amsat/steps/20.jpg)
![MoPower Cable](https://countingfromzero.net/amsat/steps/21.jpg)
![MoPower Cablep](https://countingfromzero.net/amsat/steps/22.jpg)

 If a DC power pack is plugged into the MoPower board, unplug it.  Put the stack back together (Solar power board, MoPower board, Pi Zero W, and Digital Transceiver board). Connect the Vin2 connector to J4.  With the RBF pin inserted and the Pi powered up, plug the power pack into the barrel connector on the PCB and verify that the battery pack is charging by typing:

`mpcmd ADC_VIN_VOLTS`

You should see a voltage such as this:

`*ADC_VIN_VOLTS=15.120`

which indicates that the battery is charging by the DC power pack through the Solar Power Board.  Check the battery voltage by typing:

`mpcmd ADC_VBATT_VOLTS`

You should see a value between 9 and 7.5 Volts.  If it is close to 7.5 Volts, you should charge for a while until the battery voltage is above 8 V.

8. Remove RBF pin removed and with the solar panels not illuminated, read the input voltage again by typing `mpcmd ADC_VIN_VOLTS`.  You should see a voltage close to zero.  Note the battery voltage by typing `mpcmd ADC_VBATT_VOLTS`.  Illuminate at least one solar panel, and check the charging voltage by typing `mpcmd ADC_VIN_VOLTS`.  You should read a voltage that is slightly lower than the battery voltage - this indicates that the solar panel is supplying power to the Simulator.

9. Unplug the battery from the MoPower board and plug it into one connector of the Battery Monitoring cable.  Measure the voltage at the other connector of the Battery Monitoring cable.  You should read around 9 V, positive is the smaller connector, negative, the larger connector.  If the voltage and polarity are correct, plug this end of the Battery Monitoring cable into the MoPower battery connector.  Check the voltage `mpcmd ADC_VBATT_VOLTS` to verify that it is connected.  Run the Sensor only software `python ~/CubeSatSim/python/telem.py` and you should see a row for the battery:

`Battery (0x45) v= 9.472 V i= -6.29268292683 mA p= 59.2682926829 mW`

You might see `v=0` in which case you need to unplug the battery and the MoPower board and switch the connectors - then you should see both a voltage and current.  The negative current indicates that the battery is being charged. Unplug the DC power in or remove the RBF pin with the solar panels not illuminated.  Check the battery voltage again `python ~/CubeSatSim/python/telem.py` and you should see something like:

`Battery (0x45) v= 9.092 V i= 129.091463415 mA p= 1022.56097561 mW `

`5V Supply(0x4a) v= 5.088 V i= 200.990853659 mA p= 852.134146341 mW `  

The battery voltage will be slightly lower than previously since it was under charge then and now is under load.  The current will be positive and large since the battery is supplying all the power to the Simulator.  With the power from the batter (1023 mW in my example) and the 5V power to the Simulator (852 mW in my example), we can calculate the efficiency of the MoPower UPS board (83% in this example).

11. Remove the RBF pin and illuminate at lease one solar panel.  Now look at the telemetry `python ~/CubeSatSim/python/telem.py`

`X+ (0x40) v= 3.212 V i= 121.298780488 mA p= 389.634146341 mW `

`Y+ (0x41) v= 1.256 V i= -0.201219512195 mA p= 0.0 mW `

`Z+ (0x44) v= 1.248 V i= -0.0914634146341 mA p= 0.0 mW `

`Battery (0x45) v= 9.048 V i= 95.8902439024 mA p= 758.414634146 mW `

`5V Supply(0x4a) v= 5.08 V i= 197.027439024 mA p= 939.024390244 mW` 

The battery current and power have dropped (from 129 mA to 95 mA, and 1022 mW to 758 mW) since the solar panel is supplying 390 mW.  Your Simulator is fully functional!  

12. Mount everything inside the frame and verify functionality.

13. On the Pi, run the ./radioafsk application and note the telemetry.  Vary the illumination level and position, and you should see that reflected in the telemetry.

14. Place the Sim on the turntable in front of the halogen lamp and switch on to lowest rotation rate.  Capture the telemetry and analyze using the spreadsheet.  You should be able to calculate the rotation rate of the Sim based on the period of the solar panel current waveforms.



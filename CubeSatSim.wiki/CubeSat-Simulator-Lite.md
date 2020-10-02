If you don't have the time or the money to build a CubeSat Simulator with real telemetry, you could build a CubeSat Simulator Lite.

Actually, if you have a Raspberry Pi (any model), there's nothing to build - you just need to download some software and install an antenna on one of the GPIO pins and you can receive simulated telemetry on any FM radio.

Here's the instructions. On your Raspberry Pi, run:

`sudo apt-get install git`

Answer 'y' if prompted `Do you want to continue? [Y/n]` to install git.

`git clone https://github.com/alanbjohnston/CubeSatSim.git`

`cd CubeSatSim`

`sudo apt-get install libsndfile1-dev`

Answer 'y' if prompted `Do you want to continue? [Y/n]` to install the library.

`git clone https://github.com/ChristopheJacquet/PiFmRds.git`

`cd PiFmRds/src `

`make`

`cd ../../`


Then, to start the FM transmitter, run:

`sudo ./PiFmRds/src/pi_fm_rds -audio wav/cw.wav`

or

`sudo ./PiFmRds/src/pi_fm_rds -audio wav/afsk2.wav`

Tune to 107.9 MHz on any FM receiver and you will receive recorded telemetry from the CubeSat Simulator!

Note: if you have a station on 107.9 (as I do here), then pick an open frequency (for example, 107.5 MHz), and run:

`sudo ./PiFmRds/src/pi_fm_rds -audio wav/cw.wav -freq 107.5`

The simulator can be configured to automatically start transmitting on startup by following these instructions.

Find out the private IP address of your Raspberry Pi by typing `ifconfig` when there is no network connected (i.e. WiFi disabled or disconnected and no Ethernet connection.)  Note this address as 169.xxx.yyy.zzz where xxx, yyy, and zzz are numbers 1-255.


### Instructions for Starting Up CubeSatSim Lite

1. Connect the power supply to the CubeSat Simulator Lite.  If it is a powerbank, might also need to press the on button on the powerbank.  When the Pi starts up, you will see a red LED on solidly and a green LED that flickers.

2. Wait 10 seconds then listen for AFSK telemetry on 107.907 MHz NBFM 20kHz bandwidth. (See section on [Ground Station](GroundStation) setup, except tune to 107.907 MHz.  You can also use an FM radio to hear it.)

3. If you are receiving the telemetry on your SDR software on your ground station PC, run AFSK1200Decoder (with VBCable configured) and you should see telemetry decode beginning with “hi hi ...”

### Instructions for Shutting Down CubeSatSim Lite

1. To shutdown the Raspberry Pi safely, you need a PC with PuTTY installed and an Ethernet cable.  

2. Disable WiFi on the laptop. Go to a web page and verify nothing loads `No internet`. Plug Ethernet into Pi and into laptop. You should see yellow and green lights on Pi Ethernet jack.  

3. Open Putty on PC. In Host Name type `169.xxx.yyy.zzz` and leave port set to 22. Click Open button.

4. If this is the first time you have done this on your PC, you will see the PuTTY SSH security alert, as shown above.  Click Yes to continue and you will get a black Raspberry Pi window.

5. When black Pi window opens at prompt `login as:` type `pi` then return. For `password:` type `raspberry` then return (all lower case). 

6. Once logged into the Pi, at prompt `pi@raspberrypi:` type `sudo shutdown now` then return.

7. The green LED will blink for a few seconds then go dark.  The FM transmissions will stop. It is now safe to turn off the powerpack or unplug the power cord to power off the Pi. The red LED on the Pi will go out.  PuTTY will pop up an error `Putty Fatal Error` which is normal. You can now close Putty, unplug the Ethernet cable and turn WiFi back on the laptop.  

Back to the [CubeSat Simulator Wiki Home](Home)
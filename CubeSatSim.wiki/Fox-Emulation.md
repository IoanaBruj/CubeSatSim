If you are using the new beta Transmitter/Filter Board and an experimental Fox Emulation mode software branch (such as fox) then you can use FoxTelem to receive and decode telemetry by following these instructions.

You have the [new beta Transmitter/Filter Board if you built this.](TFB)

To run the experimental Fox Emulation mode software,  SSH into your Pi and type:

`cd ~/CubeSatSim`

`sudo apt-get update`

`sudo apt-get install libcurl4-openssl-dev`

`git checkout fox`

`make`

`./demo.sh`

You will need a particular version of FoxTelem.  Go to the directory https://github.com/alanbjohnston/CubeSatSim/tree/fox/spacecraft and note the highest version number in the directory.  Then go to https://www.g0kla.com/foxtelem/downloads/test/ and download that version number.  Unzip the files and run that version of FoxTelem.

if already have FoxTelem installed, you will get message about updating files - say yes.  If haven't already had FoxTelem installed, you will be prompted about a directory location for your data, and if you want to add various spacecraft - say yes.

Now, download the two CubeSat Simulator .MASTER files from the Github Directory https://github.com/alanbjohnston/CubeSatSim/tree/fox/spacecraft  that correspond to the version of FoxTelem that you are running.  You can do this by opening the particular .MASTER file, then right click on the Raw button and select Save Link As... and save them in the spacecraft folder of your FoxTelem software folder.  

In FoxTelem, select the menu Spacecraft/Add then select the CubeSat Simulator .MASTER files that you downloaded.  You should then see a CubeSat Simulator FSK tab and a CubeSat Simulator BPSK tab - this is because we use different Fox ids for the two different telemetry modes.  The FSK mode emulates Fox-1A, 1B, 1C, and 1D, while the BPSK mode emulates Fox-1E and HuskySat-1.

In the Input tab, select RTL SDR with FSK DUV selected and IQ button (you will need to have your RTL-SDR plugged into a USB port). 

Set the Center Frequency as 434900 and then click Start

Drag the bottom of the FoxTelem window down and the FFT spectrum plot window will appear.  You should see a telemetry signal from your CubeSat Simulator.

Watch for Frames and Payloads counts to increment in bottom right corner of window.

Click on the CubeSat Simulator FSK tab.  

At the top right, you should see Telemetry Payloads Decoded showing the number of payloads you have decoded.

At the bottom, click on the "Display Raw Values" box.  At a minimum, you should see a non-zero value under Computer Temperature (if you divide by 10, you will get the Raspberry Pi CUP temperature in degrees C).

Click on the Computer Temperature value to see a real-time graph.

The time axis shows the Uptime, the time in seconds since the Raspberry Pi was last rebooted, and the Resets, a count of the number of times the software has been run on the Pi.

In the Input tab, click Stop.  Click yes to the popup asking if you want to Stop decoding while pass in progress.

Select BPSK Costas then click Start.

Watch for Frames and Payloads counts to increase in bottom left corner of window.

Click on the CubeSat Simulator BPSK tab.  If it isn't already checked at the bottom, click on the "Display Raw Values" box.  At a minimum, you should see a non-zero value under Computer Temperature (if you divide by 10, you will get the Raspberry Pi CUP temperature in degrees C).

Click on the value to see a real-time graph.





A Raspberry Pi 3B or 3B+ can be used as a Ground Station for the CubeSat Simulator.

This assumes you have setup and configured your [Raspberry Pi Ground Station](Raspberry-Pi-Ground-Station-Setup).

## SSH Access to the Raspberry Pi

In order to connect to the Raspberry Pi Ground Station, you will need SSH client software.  This is built in to Linux and Mac computers, but on Windows, you will need to download and install PuTTY.  Follow the instructions here https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html

Make sure your Pi is connected to a network, either wired Ethernet or WiFi.  Make sure SD card is inserted in the Raspberry Pi and the RTL-SDR with an antenna is plugged into a USB port.  Connect your Raspberry Pi power supply. Your Pi will turn on as soon as power is supplied. 

![Pi Ground Station](https://countingfromzero.net/amsat/PiGroundStationRunning.jpg) 

After about 30 seconds, you will be able to login using SSH.

In order to login to the Pi, you will need to be connected to the same network as the Pi and you will need to know the IP address of the Pi. 

Run your SSH client or open PuTTY.  In the Hostname or IP Address field, type in the address of the Pi.  Leave the port at the default of 22.   

![PuTTY Configuration](https://countingfromzero.net/amsat/PuTTYConfig.PNG)

Click the Open button, and a black window will open and prompt you for a username.  Type `pi` then hit enter.  Next, enter the password.  

![PuTTY Logging In](https://countingfromzero.net/amsat/Login.PNG)

You should see a login message - you are now connected to the Pi in a Terminal window.

![PuTTY Logged In](https://countingfromzero.net/amsat/LoggedIn.PNG)

## Automatic Telemetry Decoding 

Once you have used PuTTY to SSH into the Raspberry Pi, you can run the auto decode script.  When you have a command prompt, such as  `pi@pi-003:`  type 

`cd` 

`./decode.sh`

![Auto Decode Starting](https://countingfromzero.net/amsat/DecodeStarting.PNG)

If the CubeSat Simulator is transmitting telemetry, you will see packets decoded like this:

![Auto Decoding Telemetry](https://countingfromzero.net/amsat/DecodeRunning.PNG)

After you have enough packets decoded, hit Control-S to pause the decoding and scrolling.  You can then select and copy and paste them into a spreadsheet for analysis.  Note that it is important that the highlighted text for copying begins with the header "APRS:..." and ends with the telemetry data "6XX" where XX is either 49, 50, or 51, as shown here:

![Decode Copying](https://countingfromzero.net/amsat/DecodeCopy.PNG)

Hit Control-Q to resume decoding, although you will have missed the packets during the pause.  When you are finished gathering telemetry data, hit Control-C to quit or close the Terminal window.

![Decoding Stopped](https://countingfromzero.net/amsat/DecodeStopped.PNG)

## Running OpenWebRX SDR on Raspberry Pi

You can also run the OpenWebRX SDR software on the Raspberry Pi.  Then, instead of running SDR# and having to install the RTL-SDR drivers on your laptop, any laptop can just use a browser to access the SDR functionality and listen or decode telemetry.

To run the SDR, in a command window type:

`cd` 

`./sdr.sh`

You will see the script startup:

![SDR Starting](https://countingfromzero.net/amsat/SDRStarting2.PNG)

On your laptop connected to the CubeSatSim WiFi, or another laptop, open a web browser such as Chrome or Firefox.  In the address bar type the IP address of the Pi from before (192.168.8.xxx) then type :8073 then hit enter.  The OpenWebRX web page should load as shown here.

![OpenWebRX Starting](https://countingfromzero.net/amsat/OpenWebRXStarting.PNG)

Click on the triangle to start, and you should see the waterfall.  Sometimes, especially if you are running Raspbian Buster, this may take more than a few seconds for the waterfall movement to start.

If your CubeSat Simulator is running and transmitting telemetry, you should see data packets arriving, looking like this:

![OpenWebRX Started](https://countingfromzero.net/amsat/OpenWebRXStarted.PNG)

Click on the middle of the packets to move the tuner (Yellow line near the frequency) to tune the telemetry.

![OpenWebRX Tuned](https://countingfromzero.net/amsat/OpenWebRXTuned.PNG)

If you are running the browser on your Raspberry Pi, you will hear the sound on your HDMI monitor or on the headphone jack on the Pi (VNC does not relay sound).  

If you are using your PC, and your Speaker or headphone is the Default Playback Device in the Windows Sound control panel, you will hear each data packet as it arrives.  If you have VBCable installed and configured, if you make the Cable Input the Default Playback Device in the Sound control panel, and the Cable Output the Default Recording Device in the Sound control panel, then AFSK 1200 Decoder should decode the telemetry packets.  You should be able to follow the steps in [Decoding Telemetry](Decoding-Telemetry).

If the openwebrx process quits (or the Terminal window where it is running is closed) while the web page is open, the waterfall will stop moving, and you will get a WebSocket error in red in the bottom left corner

![OpenWebRX Stopped](https://countingfromzero.net/amsat/OpenWebRXStopped.PNG)


## VNC Graphical Remote Access to the Raspberry Pi

VNC is a great way to remotely access your Pi Ground Station from your laptop or PC.  Download and install the software from https://www.realvnc.com on your laptop.  Run the VNC Viewer after joining the CubeSatSim Wifi. On the Connect line, enter the IP address of the Pi then enter (you can also include a colon and the default port 5900, but you don't have to:

![VNC Client](https://countingfromzero.net/amsat/VNCClient.PNG)

You will get a Connecting message

![VNC Connecting](https://countingfromzero.net/amsat/VNCConnecting.PNG)

If this is your first time connecting, you will be prompted for the username (pi) and password of the Pi:

![VNC Auth](https://countingfromzero.net/amsat/VNCAuth.PNG)

Once connected, you will see the Raspberry Pi deskop as if you have an HDMI monitor connected!

![VNC Connected](https://countingfromzero.net/amsat/VNCConnected.PNG)

Note that VNC does not give you access to the sound from the Raspberry Pi.

## Analyzing Telemetry on the Raspberry Pi

Once you have a graphical interface such as VNC to access your Pi, or if you have an HDMI monitor, and USB keyboard and mouse plugged into your Pi, you can analyze the telemetry directly on your Pi Ground Station.  However, it is generally a lot easier to do the spreadsheet analysis on another laptop, but SSH into the Pi Ground Station to decode the telemetry.  However, this is an option.

The Raspberry Pi comes with LibreOffice Calc pre-installed, you can use the spreadsheet directly in the Raspberry Pi.  You will need to use the Raspberry Pi Desktop, so you will either need to use VNC to login (see above) or connect an HDMI monitor, and USB mouse and keyboard to the Raspberry Pi.

Run Office/LibreOffice Calc using the Desktop by clicking on the Raspberry, Office, LibreOffice Calc:

![LibreOffice Calc Starting](https://countingfromzero.net/amsat/LibreOfficeCalcOpening.PNG)

Open the CubeSat Simulator Telemetry spreadsheet by clicking Open - you should see at least one TLM spreadsheet.

![LibreOffice Calc Opening Spreadsheet](https://countingfromzero.net/amsat/LibreOfficeCalcOpeningFile.PNG)

Save the spreadsheet under a different filename, and you are ready to paste in decoded telemetry.

![LibreOffice Calc Ready](https://countingfromzero.net/amsat/LibreOfficeCalcReady.PNG)

You can run a terminal window by clicking on a black window icon at the top and type `cd telem` then `./autodecode.sh` to decode the telemetry.

![VNC Telemetry Received](https://countingfromzero.net/amsat/TelemReceiving.PNG)

After enough telemetry has been decoded, hit Control-S to pause the decoding and scrolling.  Then highlight the desired telemetry, and right click and select Copy. It is important that the text block copied begins with the header "APRS:..." and ends with the telemetry date "6XX" where XX is 49, 50, or 51, as shown in this figure:

![Decode Copying](https://countingfromzero.net/amsat/DecodeCopy.PNG)

Hit Control-Q to resume decoding, although you will have missed the packets during the pause.

![VNC Copying Telemetry](https://countingfromzero.net/amsat/TelemCopy.PNG)

Click on LibreOffice Calc (or open) and select the Data Input tab, top left cell.  Right click and select Paste

![VNC Telemetry Paste](https://countingfromzero.net/amsat/TelemPaste.PNG)

Click on OK to select the default options:

![VNC Paste OK](https://countingfromzero.net/amsat/TelemPasteOK.PNG)

The telemetry data will be pasted in the spreadsheet:

![VNC Telemetry Pasted](https://countingfromzero.net/amsat/TelemPasted.PNG)

Click on the Current tab, and wait for the graphs to be drawn and displayed:

![VNC Current Graph](https://countingfromzero.net/amsat/TelemCurrent.PNG)

To graph new data, you will need to highlight the old data in the Data Input tab and right click to Clear Contents:

![VNC Clear Contents](https://countingfromzero.net/amsat/TelemClearContents.PNG)

Click OK to accept the defaults and clear the contents:

![VNC Cleared Contents](https://countingfromzero.net/amsat/TelemClearedContents.PNG)









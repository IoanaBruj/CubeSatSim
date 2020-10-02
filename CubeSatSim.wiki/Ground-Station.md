There are a number of options for a ground station for a CubeSat Simulator.

# CubeSat Simulator Lite Ground Station

If you are looking for a ground station for the CubeSat Simulator Lite, then any FM radio will work.  Alternatively, an SDR ground station, as described in the next section, tuned to Wide Band FM (WFM) will also work.

# CubeSat Simulator Ground Station

Any 70cm ham radio that receives FM can be used to receive the AFSK telemetry from the CubeSat Simulator. In addition,  you will need a Terminal Node Controller or TNC, which interprets the AX.25 packets.  However, in order to decode and interpret the telemetry, a PC running SDR (Software Defined Radio) is preferred.  In this case, the TNC is just software, as is the radio demodulation.

# PC with a SDR USB Dongle Ground Station

Any laptop or PC with an SDR USB dongle can act as a ground station for the your CubeSat Simulator.  For example, on Windows, the SDR# free software and the RTL-SDR USB dongle ($22 on Amazon) is a good choice.

Here are the [Instructions for Configuring the SDR Software](SDR-Ground-Station-Configuration). 

# Raspberry Pi Ground Station

A Raspberry Pi 3B with an SDR USB dongle makes a good ground station too.  The OpenWebRX SDR can be run on the Pi, along with an automatic AFSK 1200 decoder for decoding telemetry.

Here are the [Instructions for Configuring a Raspberry Pi Ground Station](Raspberry-Pi-Ground-Station-Setup)

# Ground Station in an OpenWrt Router

Here are the instructions for [Configuring a GL-AR150 Open-Source OpenWrt Router as a Ground Station](GL-AR150-WiFi-Router-as-a-Ground-Station)

# Web SDR Ground Station using OpenWebRX

You can also use a Web SDR Ground Station so that others can connect to your SDR using just a web browser and can monitor and decode the telemetry as if the ground station was running on their PC.

Here are the steps:

Boot up an Ubuntu PC.  For example, if you have windows and a USB memory stick, you can create a bootable device to run or install Ubuntu https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows

Open a Terminal Window.  (At bottom left corner, click on Show Applications button then type terminal in search box at the top.

You will need to type `y` to confirm install of packages.

You may be prompted for the password.

Copy and paste these commands into the terminal window:

`sudo apt install python`

`sudo apt-get install build-essential git libfftw3-dev cmake libusb-1.0-0-dev`

`sudo apt install git`

`git clone git://git.osmocom.org/rtl-sdr.git`

`sudo apt-get install libusb-1.0-0-dev`

`cd rtl-sdr/`

`mkdir build`

`cd build`

`cmake ../ -DINSTALL_UDEV_RULES=ON`

`make`

`sudo make install`

`sudo ldconfig`

`cd ../..`

`sudo bash -c 'echo -e "\n# for RTL-SDR:\nblacklist dvb_usb_rtl28xxu\n" >> /etc/modprobe.d/blacklist.conf'`

`sudo update-initramfs -u` 

`sudo rmmod dvb_usb_rtl28xxu `

`git clone https://github.com/simonyiszk/openwebrx.git`

`git clone https://github.com/simonyiszk/csdr.git`

`cd csdr`

`sudo apt-get install  libfftw3-dev`

`sudo apt-get install g++`

`make`

`sudo make install`

`cd  ../openwebrx`

`cp ../CubeSatSim/groundstation/config_webrx.py .`

`sudo ./openwebrx.py`


These steps are from [OpenWebRX https://sdr.hu/openwebrx](https://sdr.hu/openwebrx) .

Back to the [CubeSat Simulator Wiki Home](Home)

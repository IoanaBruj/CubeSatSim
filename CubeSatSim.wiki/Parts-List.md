## Parts List

This Parts List is for the CubeSat Simulator  Three Board Stack.  There is a separate parts list for the Solar Power Board.  Here is a complete [Bill of Materials including ordering links](https://cubesatsim.org/bom).

Here are all the parts:

![Three Board Stack Parts](https://countingfromzero.net/amsat/TFB/three_board_stack_parts2.jpg)

* Raspberry Pi Zero W CPU (can be purchased as a kit, but don't get one with the GPIO header installed. Any Pi 3 will also work although it will draw much more current from your solar panels) https://www.raspberrypi.org/products/raspberry-pi-zero-w/ You will also need a 2x20 stackable header - see below.) Mini HDMI to HDMI adapter cable (so you can connect your Pi to a monitor, a right angle one is handy but not necessary). Micro USB Male to USB Female adapter cable, also known as an OTG cable (so you can connect a keyboard or mouse, a right angle one is handy but not necessary). I recommend the Argon Forty Barebones or Basic kits.  Make sure you get the Pi Zero W model (otherwise you won't have WiFi). The Barebones kit includes good USB and HDMI adapter cables.  The Basics kit also includes a camera adapter.  The Complete Starter Kit also includes an 8GB micro SD Card and a power supply (you don't need the power supply if you have the MoPower UPS V2 board).

* 16GB micro SD Card with Raspian Stretch (we recommend Raspbian Stretch or Raspbian Buster or NOOBS so you can install Raspbian  https://www.raspberrypi.org/downloads/raspbian/)

* 2x20 pin stackable header GPIO, Quantity: 2 (needed for the Pi Zero W and the MoPower V2 UPS board) 

* Transmitter/Filter Board.  Here are the parts and instructions for [building it](New-Transmitter-Filter-Board-Hardware-and-rpitx-Software-Install).

* MoPower V2 UPS board for Pi (http://www.allspectrum.com/mopower/ Order the Add-On INA219 Current Sensor so that you can monitor the 5 V power rail current supply. In your order notes, ask for a board without the GPIO header installed - this will save you having to unsolder it.  You will also need a 2x20 stackable header - see below.)

* AC/DC power adapter 15V (order with the MoPower to ensure compatibility)

* 9V NiMH battery

* 2.5mm PCB standoff set (sizes: 2x 20mm, 18x 11mm, 8x 5mm, 4x 11mm fully threaded, 10x nuts, 4x screws)

* OpenWrt WiFi Hub (GL-iNET GL-AR150 or similar). If you have a WiFi hub then you don't need this, but having one dedicated to the CubeSat Simulator makes it completely portable.  It comes with a USB cable, but you will also need an Ethernet cable and a USB wall adapter.

* RTL-SDR USB dongle for PC ( https://www.rtl-sdr.com/ or other SDR dongle such as FUNcube, AirSpy, LimeSDR Mini, etc) 

* Ethernet cable

* SMA Antenna 433MHz, Quantity: 2

The assembled Three Board Stack:

![Three Board Stack Assembled](https://countingfromzero.net/amsat/TFB/TFBThreeBoard.JPG) 

Here's how to build the [Three Board Stack](Board-Stack-Build).

Here's how to [Install and Configure the Software](Software-Install).

Back to the [CubeSat Simulator Home Page](home)
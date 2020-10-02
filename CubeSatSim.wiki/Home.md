# Welcome to the AMSAT® CubeSat Simulator Project Wiki

The CubeSat Simulator is a low cost satellite emulator that run on solar panels and batteries, transmits UHF radio telemetry, has a 3D printed frame, and can be extended by additional sensors and modules.  This project is sponsored by the not-for-profit [Radio Amateur Satellite Corporation, AMSAT®](https://amsat.org).

Here you will find documentation about this project and detailed install instructions.

Important Note: A new version of the CubeSat Simulator is in the works.  The code and Wiki instructions will be updated by April.

- Redesign by Alan Johnston, KU2Y, Jim McLaughlin, KI6ZUM, and David White, WD6DRI

- FoxTelem telemetry decoding

- STEM Payload board with STM32F103C8T6 “Blue Pill” Arduino compatible & sensors

- Tape measure monopole or SMA antenna

- Integrated Band Pass Filter

- New frame and solar panels

![CubeSat Simulator 1U Frame](https://countingfromzero.net/amsat/NewCubeSatSim2.JPG)  

If you don't have the time or money to build a CubeSat Simulator that transmits real telemetry, you can build a [CubeSat Simulator Lite](CubeSat-Simulator-Lite)!

Here are the four boards that make up the complete board stack.  Left to right: custom solar panel board, Raspberry Pi Zero W, MoPower UPS V2, and Transmitter Filter Board (TFB).

![4 Boards of CubeSat Simulator](https://countingfromzero.net/amsat/TFB/flat_cubesatsim3.jpg)

Here is the built board stack

![CubeSat Simulator Board Stack](https://countingfromzero.net/amsat/TFB/TFBBoardStack.JPG)

The build has two main parts. First, a Three Board Stack made up of two off-the-shelf boards (Raspberry Pi Zero W CPU and MoPower UPS V2) and the Transmitter/Filter Board (TFB), then the software install.  This is pictured here:

![Three Board Stack](https://countingfromzero.net/amsat/TFB/TFBThreeBoard.JPG)

Second, building the custom Solar Power Board, pictured here:

![Solar Power Board vB2 Built](https://countingfromzero.net/amsat/solar-power-board_vB2.jpg)

Third, there is a 3D printed frame, including solar panels:

![Solar Power Board vB2 Built](https://countingfromzero.net/amsat/frame_complete.JPG)

[Parts List to build the Three Board stack for the CubeSat Simulator](Parts-List). 

Instructions to build the [Three Board Stack](Board-Stack-Build).

[Software Install](Software-Install) Instructions to build and install the software for the CubeSat Simulator Three Board Stack.

Instructions to [Build the Solar Power Board](Solar-Power-Board).

Instructions for [Testing and Using the Solar Power Board](Solar-Power-Board-Testing-Instructions).

You will need to [3D Print a Frame](CubeSat-Frame) and setup a [Ground Station](Ground-Station).







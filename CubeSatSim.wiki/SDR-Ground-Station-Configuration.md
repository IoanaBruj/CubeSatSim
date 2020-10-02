Here are the steps to configure an SDR ground station with Windows, SDR#, and an RTL-SDR SDR dongle.

First, download the RTL-SDR drivers by following the steps here: [https://www.rtl-sdr.com/rtl-sdr-quick-start-guide/](https://www.rtl-sdr.com/rtl-sdr-quick-start-guide/)  Note that you need to install the x32 drivers for the RTL-SDR NOT the x64 drivers - I don't know why but it may have to do with the fact that SDR# is a 32 bit application.

Next, download the free SDR# application

https://airspy.com/?ddownload=3130

Extract all files (will go into an sdrsharp-x86 folder)

Run SDR# (SDRSharp.exe).  Under "Source:" select "RTL-SDR (USB)". Click on the triangle Play button to listen to the radio.

To use SDR# for the first time, see this video https://youtu.be/YZqpQuk8Gzw 

The next step is to [install software to decode the received telemetry](Decoding-Telemetry).

Back to the [Ground Station page](Ground-Station).
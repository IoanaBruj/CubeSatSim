This experimental command line approach automatically demodulated and decodes the CubeSat Simulator telemtry.  It is run instead of SDR#, VBCable, and AFSK 1200 Decoder.

If you haven't already installed the RTL-SDR drivers, you need to do that by downloading Zadig from https://zadig.akeo.ie and running steps 8-11 of the instructions at https://www.rtl-sdr.com/rtl-sdr-quick-start-guide/.

You will need to download rtl_fm and multimon-ng applications.

First download https://github.com/cuppa-joe/multimon-ng/releases/download/WIN32-0415/multimon-ng-WIN32.zip and extract all the files into a new folder in Documents called multimon-ng. (You might get a warning from Windows saying that this file is not commonly downloaded and may be dangerous - select Keep to continue the download.)  To extract all the files, open Windows File Manager, navigate to Downloads, and right click on the multimon-ng-WIN32.zip file and select Extract All. Alternatively, double click on the file icon, then click the Extract All button in the top left of File Manager. 

Next, download https://ftp.osmocom.org/binaries/windows/rtl-sdr/rtl-sdr-64bit-20190630.zip. Extract the files into the same multimon-ng folder.

Now run the Command Prompt in Windows (by typing Command Prompt in the Windows search bar and hitting Enter).  Change directory to the multimon-ng folder by typing:

`cd Documents\multimon-ng`

Copy the files so they are all in the same folder by typing:

`copy rtl-sdr-64bit-20190630 .`

To run the demodulator and decoder,  type:

`rtl_fm -f 440.386M -s 22050 -g 48 - | multimon-ng -a AFSK1200 -A -t raw -`

and if the CubeSat Simulator is transmitting on that frequency, you should see frames of telemetry displayed. If your Simulator is transmitting on a slightly different frequency than 440.386 MHz, then you might need to adjust the -f frequency parameter in the command.

To cut and paste the telemetry, highlight the frames of telemetry and copy (Control-C) then paste into the "MultiMon Input" tab of the CubeSatSim TLM Experimental.xlsx spreadsheet https://github.com/alanbjohnston/CubeSatSim/blob/master/spreadsheet/CubeSatSim%20TLM%20Analysis%20-%20Experimental.xlsx 

Note that SDR# cannot be running at the same time as rtl_fm.  If SDR# is running or you haven't installed the RTL-SDR drivers (see above), then you will get an error.

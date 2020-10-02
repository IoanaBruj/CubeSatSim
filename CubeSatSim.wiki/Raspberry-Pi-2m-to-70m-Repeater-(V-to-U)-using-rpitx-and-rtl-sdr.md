These instructions are adapted from http://zr6aic.blogspot.com/search/label/Repeater

First make sure your Raspbian is fully up to date:

sudo apt-get update
sudo apt-get upgrade

Note: these instructions have been tested with Raspbian Stretch on a Pi 3B - they have not been tested with Buster.  I don't think the Pi 4B works with rpitx yet.

sudo apt-get install rtl-sdr

Plug in your RTL-SDR into your Pi and test it:

rtl_test

You should get a message similar to this:


Found 1 device(s):
  0:  Realtek, RTL2838UHIDIR, SN: 00000001

Using device 0: Generic RTL2832U OEM
Found Rafael Micro R820T tuner
Supported gain values (29): 0.0 0.9 1.4 2.7 3.7 7.7 8.7 12.5 14.4 15.7 16.6 19.7 20.7 22.9 25.4 28.0 29.7 32.8 33.8 36.4 37.2 38.6 40.2 42.1 43.4 43.9 44.5 48.0 49.6
[R82XX] PLL not locked!
Sampling at 2048000 S/s.

Info: This tool will continuously read from the device, and report if
samples get lost. If you observe no further output, everything is fine.

Reading samples in async mode...


If you get an error then something went wrong with your install, or your RTL-SDR isn't plugged in.  Hit Ctrl-C to exit.

Now install rpitx

git clone https://github.com/F5OEO/rpitx.git

If you get a message saying git isn't found, then you can install it by:

sudo apt-get install git

Then go back and run the git clone command again.

cd rpitx

./install.sh

(Takes a while). It will prompt you if you want to modify /boot/config.txt file. Type a y and the script will complete.  You will need to restart your Pi for the changes to take effect.  Do this by typing:

sudo reboot now

After rebooting, you will need to log in again, then type:

cd rpitx

If you have built a Transmitter/Filter Board with a Band Pass Filter at 433 MHz, then you can test out the transmitter by typing:

(while true; do cat sampleaudio.wav; done) | csdr convert_i16_f | csdr gain_ff 7000 | csdr convert_f_samplerf 20833 | sudo ./rpitx -i- -m RF -f 434.9e3

If you tune to 434.900 MHz NFM, you should hear the Gettysburg Address being read.  Hit Ctrl-C to exit.

Now, you can put both of these together with this command:

sudo rtl_fm -s 48000 -g 0 -l 0 -M fm -f 146550000 | csdr convert_i16_f | csdr gain_ff 12000 | csdr convert_f_samplerf 20330 | sudo ./rpitx -i- -m RF -f 434.9e3

You should see the FM carrier at 434.900 MHz.  If you transmit FM on 146.550 MHz, you should hear it repeated at 434.900 MHz.

If you don't, then test out the two parts separately.

To test the receiver, type this:

sudo rtl_fm -s 48000 -g 0 -l 3 -M fm -f 146550000

This sets the squelch level to 3 (-l 3).  When you transmit on 146.550 MHz, you should get a bunch of gibberish on the screen.  It should stop when you stop transmitting.  If you get this, then your receiver is working.  If you don't, then maybe your antenna on the RTL-SDR isn't working, or your transmitter isn't on the right frequency.

If that works, test again your transmitter:

sudo ./rpitx -i- -m RF -f 434.9e3

You should hear the carrier at 434.900 MHz.

Then put both commands together to get the repeater working:

sudo rtl_fm -s 48000 -g 0 -l 0 -M fm -f 146550000 | csdr convert_i16_f | csdr gain_ff 12000 | csdr convert_f_samplerf 20330 | sudo ./rpitx -i- -m RF -f 434.9e3




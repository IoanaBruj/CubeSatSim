Installing RTL-SDR drivers on a computer can be complex, and is not possible on some operating systems.  An alternative is to plug the RTL-SDR into an inexpensive OpenWrt WiFi Router using this simple installation procedure.  SDR applications across all operating systems support connecting to an RTL-SDR over a network connection, which could be the WiFi of the router or the LAN Ethernet port.

The GL-AR150 is an example of a low cost OpenWrt router that comes with OpenWrt preinstalled and has been tested with these instructions.

## OpenWrt Router Configuration

First, setup your OpenWrt router.  These instructions are for the [GL-AR150](GL-AR150-Open-Source-OpenWrt-Router-Configuration.)  You will need to know the administrator password.

Next you will need an SSH client such as PUTTY - download it and install it from https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html (Note: if you have a Mac or run Linux, you already have an SSH client.  Just type `ssh root@192.168.8.1` into a terminal window to connect.

Join the WiFi for the Router, open the PuTTY application, then enter this address into PUTTY as Host Name or IP address field: `192.168.8.1` then click Open.

![PuTTY Login](https://countingfromzero.net/amsat/RouterPuttyLogin.PNG)

A terminal window will open, and you  will need to enter the username of `root` and the password that you configured earlier:

![Router Logged In](https://countingfromzero.net/amsat/RouterLoggedIn.PNG)

Next, install the RTL-SDR software by typing these commands in the window, hitting Enter at the end of each line and waiting for the operation to complete:

`opkg update`

`opkg install rtl-sdr`

`opkg install librtlsdr`

Now plug the RTL-SDR into the USB port on the router.

To see if the RTL-SDR is working type:

`rtl_test`

And if you get a message that says "Found 1 device(s)..." then it is working.  Hit Control-C to exit.  If you get a "not found" error, double check that the three installation commands above didn't generate any errors, and that your RTL-SDR is plugged into the USB port on the router.

Now you need to configure the rtl_tcp server to run on startup.  

Type this command to download a file and copy it to the right location:

`wget http://countingfromzero.net/amsat/rtl_tcp.txt`

`cp rtl_tcp.txt /etc/config/rtl_tcp`

Find out the IP address of your Router by typing:

`ifconfig | grep "inet addr:" | cut -f2 -d ':'`

The first address should be the IP address -  you will need this to configure your SDR application in the next section.

Reboot the router by unplugging the power and plugging back in again. You should no longer need to use SSH or PuTTY as on boot the rtl_tcp application should automatically run.

## Testing with an SDR

On your PC, join the WiFi network of the Router, and open the SDR# software.  For Android or iOS, run the SDR application and follow their instructions for a RTL-TCP connection.

In SDR#, under the Source menu, select "RTL-SDR (TCP)".  

![SDR# Source Selection](https://countingfromzero.net/amsat/RouterSDRSource2.PNG)

Next, click on the gear icon to configure the server. 

![SDR# Source Configuration Settings](https://countingfromzero.net/amsat/RouterSDRSourceConfiguration2.PNG)

A small window called RTL-TCP Settings will open.  In the Host field, enter the IP address, such as `192.168.8.1` for my router, and leave the port at the default of 1234. The default Sample Rate of 2.048 MSPS (Mega Samples Per Second) is likely to be too high for the Router - the playback might be jumpy and start and stop, so reducing the rate will improve listening quality. Set the Sample Rate to 0.25 MSPS, the lowest setting.  

![SDR# Source Configuration](https://countingfromzero.net/amsat/RouterSDRSourceConfigurationFirst2.PNG)

Next, click the Start button (triangle at the top of SDR#).  The waterfall will start to move, but you won't see any signals since the RTL-SDR Gain defaults to 0.  Open the Configure Source RTL-SDR Settings window by clicking on the gear icon, and slide the RF gain to at least 3/4 of the way across.  Now you should start seeing signals on the waterfall.

![SDR# Source Start](https://countingfromzero.net/amsat/RouterSDRSourceConfigurationSecond.PNG)

If an antenna is connected to the RTL-SDR, you should see stations.  You can change the frequency, modulation, etc.  Each command takes a fraction of a second to complete.

If the waterfall freezes or stops responding, the WiFi router might need resetting by powering it on and off.







 



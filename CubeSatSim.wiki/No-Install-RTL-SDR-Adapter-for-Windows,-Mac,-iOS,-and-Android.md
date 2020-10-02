RTL-SDRs are great low cost, entry level SDRs.  They are perfect for teaching, demonstrations, and for introducing to the world or radio listening.

However, using RTL-SDR on Windows requires some tricky driver installation and administrator privileges on the computer, something not everyone can do or has.  On Macs, there are aren't many options at all.

Higher priced SDRs don't require this driver installation, but they are, well, much higher priced, starting at 4x the price of an RTL-SDR.

Here is a simple solution that allows using an RTL-SDR on Windows, Mac, Linux, and even iPhone and Android phones!  And the cost is about $20, and takes only a few minutes to configure!

All you will need OpenWrt Router. My favorite is the GL.iNET GL-MT300N-V2, available for $20 on Amazon. These routers usually come with a USB to micro USB power cable, but no power plug to plug it into the wall.  If your computer has a spare USB port, you can just plug it in there and no power adapter is needed.  If you want to operate portable, you could use a USB power stick to power the Router and RTL-SDR.

All you have to do is follow the steps here to install the RTL-SDR drivers and rtl_tcp application on the Router using these instructions. 

First, configure the Router.  For mine, [These were the steps.](GL-AR150-Open-Source-OpenWrt-Router-Configuration)

Next, [install the RTL-SDR drivers and software on the Router.](RTL-SDR-on-OpenWrt-Router)

Now, you are all set! 

For laptop operation, you can use an Ethernet cable between the Router and your computer and a USB port to power the Router.  

![No Install PC](https://countingfromzero.net/amsat/NoInstallPC.jpg)

Or, you can join the Router WiFi network, although this will disrupt your existing WiFi connection.  But this has the advantage of allowing remote operation.  For truly portable operation, use a USB powerpack to power the Router.

![No Install WiFi](https://countingfromzero.net/amsat/NoInstallWiFi.JPG)

Software that I have tested and works includes:

* SDR# for Windows
* GQSDR for Linux
* SDR Receiver for iOS
* SDR Touch for Android



 
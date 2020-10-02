By setting up an account on https://remote.it and installing client software on the Pi, you can access the Raspberry Pi remotely via SSH.

First, create an account on remote.it.  Next, SSH into your Pi and install the client software:

`sudo apt-get install weavedconnectd`

Then run the installer:

`sudo weavedinstaller`

If you get a not found error (e.g. if you are running Raspbian Buster), you can do the install using apt instead of apt-get:

`sudo apt update`

`sudo apt upgrade`

`sudo apt install connectd`

`sudo connectd_installer`

When the installer runs, select 1 then enter your username and password created at remote.it.  Then give your Pi a name, then select 1 to attach it to a service.  Select 1 for SSH and say y to continue with default port.  Give the service a name, such as SSH-Pi.  Then select 4 to exit.

Now login to app.remote.it and look for the new Pi.  To login, click on the Device name, then click on the service (e.g. SSH-Pi) and you will get a hostname and port for SSH connection!



The 1U frame for the CubeSat Simulator is 3D printed. You will also need to mount the antenna on the top and the push button switch on the top as well.

Here is a [link to the STL files](https://www.thingiverse.com/thing:3613014) that you can use to print your frame.  Or, if you don't have access to a 3D printer, you can follow the "Order This Printed" link to have one printed and mailed to you 

Here are the 3D printed parts:

![3D printed parts](https://countingfromzero.net/amsat/3D_parts.JPG)

You will likely need to clean out some of the holes and notches with a knife or file before assembly.  

Here are the steps for the a particular printer (Lulzbot TAZ 6) - the steps for your printer will be similar.

1. Download and install [Cura for Lulzbot](http://lulzbot.com/Cura)

2. When you run Cura the first time, it will prompt you to install a printer - select Lulzbot TAZ 6.

3. On the upper right side of screen, it should say Lulzbot TAZ 6.  Under catagory choose All.  Under Material choose PLA (Verbatim).  Under Profile, choose Standard - 0.25mm

4. Download the STL files for frame.  We print the rails in grey and the remaining sides, top, and bottom in translucent.  Click on the Open File on the right hand side and select your downloaded file.  You will most likely have to Rotate the part until it is flat (you can't print it standing vertically - it will fall over!).  A 90 degree rotation on the X axis should do the trick.  Place and arrange the parts.  Make sure they are all on the bed - they will be a solid color when resting on the bed, and a grey cross hatched color when they are not.

5. Next to Print Setup, click the Custom button .  Scroll down and click on Material.  Scroll down and click on Support.  Make sure support is not enabled.

6. Click Save to File and save your gcode file.  Note down the print time - it is a good idea to put this in the filename as filename_xh_ym.gcode where it will take x hours and y minutes to print.

7. On the printer, load the PLA material (grey or translucent, depending on the part).  If you need to change spools, set the Nozzle temperature to 240 degrees, loosen two clamp nuts, and move the wheel backwards to back out the existing material.  Rewind remaining onto the spool and poke the end through a hole so it does not unwind.  Feed in new spool, and push through nozzle until the right color comes out.  Retighten two clamp nuts.  

8. Put your gcode file on the SD card (you might need a USB SD Card reader) and insert in the printer.  Select Print from SD and select your file.

9. Watch it start printing at least two layers to confirm that it is sticking to the bed properly before leaving.  Come back in x hours and y minutes (noted from Cura or from the gcode filename) and remove the print and take off the spool.

Carefully identify the parts.  The bottom has the + shaped opening, and the top is identified by a "T".  The side with the "T" must face the side panel with the hole for the RBF switch in it.  The sides snap into the post pieces after the bottom has been put in place.  Once the four sides have been snapped in place, test fit the top, but do not finally snap it in place.

Solder the female JST RCY connectors onto each of the solar cells, red to +, black to - side.  Hot glue the wire insulation to the solar panel - this will provide strain relief so the wires don't pull out.  It should look like this when you look down into the frame:

![3D printed parts](https://countingfromzero.net/amsat/solar_panel_glue.jpg)

You might want to test the solar cells before soldering and mounting them.  Cut four small 3mm square pieces of the mounting square for each cell and stick on the back of the four corners.  Remove the paper and stick them onto the panel.  The panels can be centered, except for the +X panel (with the hole for the RBF) which will need to be raised slightly or the holes will be covered.  Also make sure the holes and slots on the top are not covered.  The JST RCY connector wires should feed inside the frame.

Attach the SMA male to female coax and the right angle SMA adapter to the Digital Transceiver Board. 

Solder the momentary push button switch to a female JST RCY connector, ready to plug into the MoPower board.  The complete frame should look like:

![3D printed parts](https://countingfromzero.net/amsat/finished_frame.JPG)

Make sure the nut is not present on the RBF switch - it is not used.

Follow the [Assembly Instructions](CubeSat-Assembly-and-Disassembly-Instructions)


**As of the end of 2018, The Cyclone was dismantled due to lack of use and the Proxxon being better at doing PCBs.**

Mal donated an almost-working [Cyclone PCB Milling Machine](http://reprap.org/wiki/Cyclone_PCB_Factory), which has since been made to work!

# Step By Step Guides
* [[Cyclone-PCB-Start-To-Finish-Step-By-Step-Guide]]

# Software

## Toolchains Confirmed To Work
* Fritzing, design, export Gerber -> Flatcam, export gcode -> CNC Gcode Controller, machine control
* Eagle, design circuit, export Gerber -> Flatcam, export gcode -> ...?

## PCB Design
* Eagle - works, but steep learning curve, can generate Gerber files that work with Flatcam (gerber -> gcode)
* 123dcircuits.io - easy to design a circuit, but exported Gerber doesn't work with Flatcam
* Fritzing - works, is easy enough, need to work out how to get it to do single sided boards easily / by default

## Geber -> Gcode Conversion
* [Flatcam](http://flatcam.org/) looks fairly user friendly, easy to use and actively developed, tutorial on usage [here](http://diwo.bq.com/como-crear-gcode-para-fresar-pcbs-en-cyclone/): 

## Machine Control
* [CNC Gcode Controller](http://reprap.org/wiki/CNCGcodeController) looks like it should be good and has bed auto leveling support, runs okay on Windows under Java 7.  `java -jar CNC-GCode-Controller_libs.jar`.  Tutorial on usage [here](http://diwo.bq.com/cnc-gcode-controller-instalacion-y-uso/)
* Pronteface (or any 3d Printer software) can drive the machine around.

# Random links
* Thingiverse model - http://www.thingiverse.com/thing:49484
* Cyclone Google Groups - https://groups.google.com/forum/#!forum/cyclone-pcb-factory
* http://www.cyclonecnc.4fan.cz/
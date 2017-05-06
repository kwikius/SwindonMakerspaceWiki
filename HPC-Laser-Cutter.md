A page for collecting notes and information about the HPC laser cutter that we have on loan from Reprap Ltd.

# Using the cutter:

To begin with, you will want to make your drawings into a dxf file, and get it on to the computer by the cutter.  You can do this using a usb key, emailing it to yourself, sticking it on the internet somewhere... just remember that if you log in to your email, you should log back out.

Next, open the laser cutter software, which is named, imaginatively, "laser cut".  It's pinned to the taskbar.

Import your dxf file -- file/import.

Unify lines.

In the top-right corner of the program, there is a list with some colour swatches in, which match the colours of your imported dxf file.  Each of these is a sort of layer.  When you go to cut, it will start at the top of the list, cut all lines of that colour, and then move on to the next one.  You can drag-and-drop if you don't like the order.  (For example, you should try to leave cuts that will create small pieces until after the cuts that will add features to those small features.)  Each colour also has it's own settings associated with them -- type, speed, and power.  You'll want to change these to get a good cut, and the kind of cut you want.  If you want to cut shapes into your workpiece, even if you don't want to cut all the way through, leave the type on "cut".  Change the power and speeds to where you want them -- look at most of the rest of this page for starting places, but note that similar looking materials can require different settings anyway -- for example, different densities of foamboard, even if they are the same thickness, or wood with or without knots in it.  The power level is in percent.  Going over 100% will not be helpful, and seems to cause odd things to happen.  The physics of the laser mean that there's a minimum power level under which the laser doesn't fire, which seems to be around 10%.  FIXME: what are the units of speed, anyway?  There are two speeds listed -- "speed" and "corner speed".  "Speed" is how fast it moves on straight lines, and "corner speed" is how fast it moves when going around corners, which should generally be about 5 slower.  There are also some advanced settings for doing things like cutting dashed lines.  Most of these are untested and not really understood.

Go around to the chiller, lift the lid, and smell the water.  If it smells like chlorine (think swimming pool), that's good.  If it doesn't, throw in a capful of the "sterilizing fluid" that should be sitting on top of the chiller.  That keeps stuff from growing in the water cooling water, which would end up burning up inside the laser tube, where it's really hard to clean.

Flip the key-switch on the side of the laser cutter to turn it on.  This will turn on the compressor, the extractor fan on the roof, the chiller, and provide power to the fancy stainless steel extractor/filter unit.  (Which won't turn on quite yet.)  If any of that stuff doesn't turn on, something is wrong, and you shouldn't cut until everything is working properly.


# Cut Settings

Work area: 680 x 400mm

Rolls of material on roof - @TheOrbTwo

## Red cotton
* Cut: speed 200, power 30, passes 1
* Engrave (shallow): Speed 250, power 18, passes 1

## Black mesh netting
* Cut: speed 200, power 16, passes 1/2 depending on threads
* Engrave nicely: Speed 250, power 13, passes 1

## Rubbery material
* Cut  MORE TESTING REQUIRED. didnt cut fully at 250s 45p
* Engrave nicely: speed 250, power 15/15, passes 1

## Cardboard 0.22mm Thickness (UPDATE GSM value)
* Kerf value of 0.1mm (or oversize edges of design by 0.1mm)
* Cut: speed 320, power 17, passes 1
* Engrave: speed 400, power 14/13, passes 1, note corners may still pinhole due to laser power and thickness of material

## Corrugated Cardboard single wall
* Cut: speed , power , passes 1
* Engrave: speed , power , passes 1

## Fleece to cut through just support material on back. NOTE TEST on your material, fluffy side down.
* Cut: speed 250, power 13/14, passes 1/2 depending
* Engrave: speed 300, power 13, passes 1 - Engraving is useful for marking material for hand cutting.

## Thin fleece to cut through just support material on back. NOTE TEST on you material, fluffy side down
* Cut: speed 180, power 14, passes 1

## Foamboard (stuff Rob has) [link](http://www.artdiscount.co.uk/paper-board/board/foam-board/white-foam-board-5mm.html)
Still a bit sketchy on long curves for some reason, where the head goes slower than it should / does on straights.
* score: speed 250, power 18/14, passes 1
* half: speed 130, power 28/24, passes 1
* cut: speed 100, power 42/40, passes 1

## Simon's 10mm packaging foam (velvet facing)
* cut: speed 20, power 20, passes 1

## 3mm Plywood
* cut: speed 20, power 50/45, total kerf 0.2mm (use offset of 0.1)
* engrave: speed 50, power 18/14, passes 1

## 1.5mm Plywood
* cut: speed 20, power 28/26

# Initial hardware settings, main electronics bay (right side):

** Main control board, bottom board: JP6 is on pins 1-2.

*** According to the Hardware Manual 4.2, there are several more jumpers that I didn't see on my first reconnaissance mission, will check for them next time I (theorbtwo) am in the space.

** Motor controller DIP switches:

*** X: 1001 0000

*** Y: 1001 0100

*** Z: 0100 0010

The main controller itself is a Leetro MPC6525, which seems extremely common in lasers of this general sort.  http://www.leetro.com/english/sale/1-2.html is Leetro's page on it, which includes detailed documentation (download/manual/hardware manual), as well as the software / drivers (win32 only).  Also, if the sticker is to be believed, it has newer firmware.

Chapter 6 of the hardware manual is also interesting reading -- it specifies the protocol spoken between the PAD03 (front panel) and the main controller.  At the lowest level, it's standard RS232 serial, 9600bps 8N1, on a standard DE9 connector.  On top of that is Modbus RTU, which is a well-known protocol for doing this sort of thing -- http://www.modbus.org/docs/Modbus_Application_Protocol_V1_1b3.pdf is the full specification.  Chapter 6 of the hardware manual specifies the individual meanings of the "relays" (single-bit values) and "registers" (multi-bit values).

# Chiller

Our chiller is a PH-LW06-BLP/?? (FIXME: note down the ??).  http://www.wklaser.com/uploadfile/file/20150410/201504100145000.zip is a manual for that exact model, though it leaves a fair bit to the imagination.  2.2.1 defines PH-LW06-BLP/?? as being PH=Sunrise family, LW=water chiller for laser, 06=600 W cooling capacity, B=back-exhausting, L=low lift pump, P=with flow switch, /??=code for client.  

I've also found a manual for a closely related chiller at http://www.checkmatelasers.com/docs/GM/PowerHouseChillerManual.pdf, which leaves less to the imagination.  Using this information, we find the following settings:

* dC: 15 -- I believe this is the desired maximum tempurature of the output water.

* dh: 2 -- I believe this is the allowable tempurature range of the output water -- the water is allowed to be 13-15 degC.

* Pt: 1 -- Failure alarm delay, 1 minute (do not sound alarm unless temp out of range for more then 1 minute).

* Lt: 5 -- Low temp. alarm, 5 degC

* Ht: 25 -- High temp. Alarm, 25 degC

* ca: 0 -- ?

* t1: 1 -- ?

* t2: on -- ?

* f1: 1 -- ?


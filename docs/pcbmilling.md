# Milling PCB's with 3018 Chinese Desktop CNC

## Notes in advance
* This procedure is not perfect. If you need board that "just work", order them in China and wait 2 weeks. This process is for fun and educational purposes. Especially with larger PCB's, it becomes more likely that something will go wrong and the more time you'll have to spend redoing steps. If possible divide your project in smaller sub-boards with well-defined sub-tasks. 
* The process is also less precise than the chinese board houses so don't expect tiny smd components and microvias. There are more hints about what is (not) possible below.


## Drawing layout
I always use KiCad but any program that exports gerber should do. Here are some hints:

* If you can, keep it single sided. It will save a lot of hassle. 
* Start by routing things on the bottom, not all components can be soldered from the top or rotated to be mounted on the bottom. 
* The minimum trace (separation width) appears to be somewhere between 0.4mm and 0.5mm. Therefore I have configured my software to keep a minimum separation/clearance of 0.5mm in all nets and pads (20 mils). Out of laziness I have also configured a trace with of 0.5mm but the machine could do much less if asked. This is just easy for debugging and the large pads and separation make it impossible to route very complicated designs anyway.
* The machine is capable of milling down to 0805 and TQFP 0.8mm pitch SMD components. I have not tried to solder these but I guarantee that it will not be easy. Go for larger smd parts if you must. If you use 1206 or 1210 SMD parts you can likely route a signal between the pads.
* 0.8mm holes are fine for most components, whith the notable exception of pin headers, which require 0.9mm holes or larger. If you are lazy, use 1.0mm holes everywhere. It is possible to mix hole diameters on one board but if you mix many sizes, swapping the bits gets tedious. For 1mm holes, 2mm pads are the absolute minimum. For smaller holes I think you could get away with smaller pads but soldering is more comfortable at 2mm. For components that allow it (usually pcb drawing programs have this option for THT IC's readily available), long pads are recommended (they are postfixed with _HandSoldering in KiCad). 
* holes won't be plated. Of course, vias can be created with a short length of wire. Often it is possible to use component pins as vias. If you rely on a connection getting through at a component pin, make sure this component allows soldering from both sides. Most notably: pin headers cannot be soldered from the top. IC's and resisors are fine, but an led that must be mounted flush to the board cannot be soldered from the top.

## Isolation routing
I use FlatCam (version 8.5) to turn the Gerber files into gcode. It offsets the ousides of all traces by half the tool diameter and takes care of lifting the tool when travelling. There are several steps involved. I moved my pcb in kicad to be located to the upper left of the origin (this is actually outside the drawing area) before exporting. I have not found a way yet to define the origin for export in kicad (the latest includes an option to set an origin but it is only used for gerber and drill files and not for the board cutout and solder masks so that makes life harder instead of easier). Alternatively you can translate all layers in FlatCam but that needs to be repeated manually for each layer and you cannot move by drag-and-drop but are limited to typing (dx,dy).

* I export the design as gerber + excellon drill file (for holes) + svg (for board outline) + pdf (for solder masks). If you want a simple rectangular board outline you don't need to export it, FlatCam has a cutout generator that can make it for you.
* The idea of the FlatCAM user interface is that you have to double click the object in the Project pane to go to it's processing options. Depending on the type of object you'll get different options. 
* Import your gerber and double click the name in the Project pane. "Under Isolation routing" set the "tool dia" to 0.5 and click "Generate Geometry".
* Go back to the Project pane and double click the newly created isolation object. Under "Create CNC job", set cut Z to -0.1 (or -0.15 to be on the safe side), Travel Z to 2, Feed rate to 30 (60 works too), Tool dia to 0.5 and Spindle speed to 9000. 
	A single pass will work but I usually make 2 passes with 80% overlap. Then click "Generate".
* In the Project pane select the _iso_cnc geometry. There are no relevant options, just click Export G-Code.
* The drill file is straight forward. I use a cut z of -2.5, a travel z of 2, a feed rate of 60 and a spindle speed of 9000. 
* The outline can be generated in FlatCam or imported from svg. My cad programs exports svg in mils and flatcam expects cm so I have to scale by 0.00254. So far I've used a 2-flute 2mm end mills to cut the outline. First I used some straight edge mill bit but they perform terrible. I mill the outline at -2.5mm depth at multiple passes with  depth/pass at 0.2mm. Feed rate can be up to 400 (use 200 to be on the safe side) at that cut depth. You can go slower and make larger layers (upto cutting everything at once at about 10mm/min) but you get a smoother result in the same total time if you take small steps. 
* Note that it may be usefull to make these settings the default in the Options panel.


## Carve PCB
I use Candle (version 1.1.8) to send the gcode to the mill. 

* make sure the pcb is really clean. Nail polish remover works well. Soapy cleanants don't work so well. Use the green side of a sponge or even sanding paper to remove any dirt.
* don't touch the surface of the pcb with your greasy fingers after cleaning. 
* tape the pcb in the rectangular cavity of of sacrificial plate. Tape on all four sides, apply generous pressure. 
* Large pcb's tend to be not-straight. If you can see the pcb move down in a springy fashion when pushed down heightmapping will not work. Tape it down more tightly or cut the pcb to a more appropriate size first.
* Home the axes of the printer and zero the work coordinates. 
* Use the jog buttons to move the drill over the place where you want the origin to be. Note down the coordinates and zero the coordinates again. The original coordinates are needed if you want to calculate the mirroring coordinates for the back. If you only have one side this is not needed. The cutout is located at (40,20) from the homing position and 170 by 120mm in size. I'm confident that you can work out the x-coordinate of the mirror line now.
* If this is the first time, then open Service>Settings and change the height of the fast-z-probe command to -10 (was -30). The new command should be "G21G91G38.2Z-10F100; G0Z1; G38.2Z-2F25". This is necessary because depending on the tool length the final probe location may end up below the -45mm machine height remembered by the firmware and trigger a virtual z-min limit switch before even starting to move down. Do note that you have to be within 10mm of the copper for the probe to succeed now.
* Make sure the probe is wired correctly. The easiest way to do this is to start a z-probe and touch the bit with the other lead. The machine should back off immediately, if it does not, abort quickly (either by red emergency button or with the soft-reset button in Candle).
* Make a z-probe in the origin and zero the z-coordinate. Jog the head up a few milimeters.
* Open up the heightmap panel on the right and click "create". I usually make a 5x5 heightmap. Click "probe" when you have configured the rectangle. 
* The map should be relatively smooth. It is possible that there is a gradient but there should not be bumps. In particular bumps or valleys that contain just one measurement indicate that that measurement may have gone wrong. You can make a manual z-probe at that location and edit the heightmap or just redo the whole heightmap. Note that the visual will always go from bright red to bright blue so look at the table to get a feeling for how much variation there is. No measurement should be more than 0.2mm off from zero and usually the maximum deviation is below 0.1mm.
* After probing, click "edit mode" to exit edit mode and "Use heightmap". You should see the whole design move a few pixels up or down.
* Hit "send" to carve the traces. 
* Jog the head up, and replace the carving tool with a drill bit. For drilling it is not necessary to make a height map. It is not even necessary to make a z-probe. Simply let the bit sit in the socket first and move the head down to approximately the right location. Make sure the bit rests on the surface and tighten the chuck a little. zero the z-coordinate in Candle. Move the head up and tighten securely. 
* I usually do: front traces > holes from the front > back traces > cutout from the front or back. As long as you stay on one side you don't need to heightmap or home again. As soon as you take the pcb off the machine you have to heightmap again. 
* For double sided pcb's, align the pcb in the bottom right. The square is not perfect. It is most important that on both sides you align the bottom of the pcb with the bottom edge of the square. Rotations cannot be compensated for. If there is a small translation error this can be corrected. On a calculator determine the coordinates of at least one of the holes that were drilled from the front in mirror coordinates. Command the mill to that location. Move the bit right over the hole. With your fingers turn the acme leadscrews a few steps until the hole is perfectly aligned. Only the x-axis should need this. With a more carefully drilled surface this should also not be necessary.
* clean up burrs by sanding very softly with the finest sanding paper around. If possible use a microscope to check if any burrs are creating bridges between zones. Using 2 passes usually prevents this very well but just check anyway. Especially check between pads. Sometimes there is only one pass between the pads. 
* use a multimeter to verify that everything is not connected is actually not connected. 

## Solder mask
* Solder resist can be aplied. I used uv hardening solder resist from aliexpress that I selectively exposed using a uv exposure box and a pattern printed on overhead transparancies.
* again, start by cleaning thoroughly. 
* A small dot of solder resist was aplied to the print after carving and drilling. I have experimented with the order of things. Getting the unexposed solder mask out of holes is tedious so it would be better to do that before drilling holes. However, holes are usefull for aligning front and back. Maybe one or two holes can be drilled outside the board for alignment? Also: it is easier to spread out the paste before cutting out the board because once it hits the wall all paste goes out at that point. I have tried applying paste before cutting but that is also not ideal because the edge of the paste tears off during cutting. Maybe this can be resolved by clearing a few mm of paste from the edge by including the edge in the resist mask.
* The solder mask paste is pushed out gently using a laser printed stencil. Then a glass plate is pushed on top to evenly  spread out until the whole surface is covered. The glass is removed and the pcb with the stencil was exposed to a uv ledstrip for 7 minutes.
* After exposure you can carefully peel the laser printed stencil away. It should come off clean in the places where it was exposed. 
* Remove the unexposed/liquid solder mask using water and an old toothbrush. You may have to push a drillbit through the holes to get them clean. The laser toner absorbs most light but not all so the stuff becomes a little sticky and thick in some places. After the majority of solder mask is cleaned up I finish the cleaning with a cotton pad with nailpolish remover. This should remove all solder mask from the pads.


# Open experiments/issues:
* try at lower spindle speed if you get less burring.
* eliminate more backlash.
* experiment with silkscreen techniques.
* experiment with other tools for milling the board outline.

# Y Axis: Draft

This modification targets to optimise the travel of the y axis and therefore increase the useable are of the machine. It is still a draft and therefore incomplete, use at your own risk.
 
## Issue

The image below shows the machine in it's default configuration, drawn to scale. It shows in black the build plate as well as  the staging plate and both rows of feeders. Additionally it shows in grey the optional 3rd staging plate in the back and a proposed 4th stating plate in the front.
 
Image
 
Overlaid are multiple rectangles, marking the usable range of the different tools on the machine head. Green marks the area which can be reached by the camera. The blue rectangle marks the area reachable by both nozzles and the red areas are only accessible by on of the nozzles.
 
Looking at his image, the issue should become rather clear: there is an area approximately 30 mm deep, spanning across the whole width of the machine, where none of the nozzles can reach. This is wasted area of the 3rd staging plate and as this simple modification demonstrates, it is wasted for no reason.
 
I'm sending out an official bottom smack to everyone at Opulo for this. Not only because it is a bad design choice but because you lie about this in the LumenPnP brochure. It states a max. PCB size of 240 x 400 mm. This is wrong because the max. usable size is more like 210 x 385 mm. And this is no more unintentional, now that I have told you.

## Proposed solution

The inaccessible area in the back of the machine can easily be eliminated, by moving all the plates 35 mm closer to the front of the machine. While 30 mm would be enough, the additional 5 mm cover potential variances for example in the assembly process of the machine. To retain all functionalities of the machine and to not break compatibility, the front feeder rail needs to move by the same amount for the feeders not to collide with the build plate. This in turn requires modifications to the front legs, as these define the position of this rail. This is the main content of this modification. 
 
There are multiple ways to solve this issue. This solution is limited to only modifying the front legs and adjusting some other machine parts, including the configuration of OpenPnP. This severely limits the scope of the modification to a local optimum and leaves many more optimizations untouched. This is chosen to maximise the accessibility of the modification for as many users as possible.
 
Other options would be to move the front feeder rail by a shorter distance because the feeder frame could be made shorter by quite a bit, as can be seen in this proposed modification. However this would break compatibility to the existing feeders as they are sold by Opulo. Additional optimization can be found by overhauling the design of the head assembly and parts of the gantry. This however is outside of the scope of this simple modification as it would involve almost completely disassembling the machine and changing the controller firmware.

## Implementation

A word of warning to begin with: this modification messes up the coordinate system, because it changes the homing fiducial position. All precise x and y coordinates become invalid, especially those of tool changer positions. Keep this in mind before you proceed.
 
To implement this modification, first of all you need to print the modified front feet. The next step is to remove the existing front feet. For that, the front feeder rail needs to be removed as well as the y axis idler pulleys together with the idler pulley arms. With that out of the way, the feet themselves can be removed. Due to the changed mounting of the front feeder rail, the angle elements, used to bolt the feeder rail to the lower y gantry rail, need do be removed.
 
Now the assembly can begin. Start by bolting one leg to the y gantry, then insert the front feeder rail into it's pocket in the leg, finally add the second leg. Now reattach the angle elements in such a way, that they connect the front feeder rail to the lower y gantry rail. Reattach the idler pulleys and tighten the y axis belts. With that completed, the most difficult part is already done. Now only the y axis striker and the leg extensions need to be transferred from the old to the new legs.
 
Now comes the fun part, which actually makes a difference now. Loosen all staging plates on the machine and realign them 75 mm away from the front feeder rail. You can do this like during the initial assembly by using the supplied jig. Now open OpenPnP and adjust the position of the homing fiducial, the bottom camera and every thing else that is bolted to the build/staging plate. Test if everything still works and enjoy the usable machine area that is now almost 10% larger.

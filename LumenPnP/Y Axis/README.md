# Y-Axis Optimisation

A Modification optimising y axis travel to increase the usable area of the machine in triple staging plate configuration by almost 10%. It involves replacing the front legs with newly printed ones, slightly rearranging the staging plates and updating the configuration of OpenPnP. It is highly recommended for Opulo to adapt this modification in one form or another.

## Issue

The image below shows the machine in it's default configuration, drawn to scale. It shows in black the build plate as well as  the staging plate and both rows of feeders. Additionally it shows in grey the optional 3rd staging plate in the back as well as a proposed 4th stating plate in the front.

![Machine Table before](https://github.com/user-attachments/assets/33d8fd97-d878-4bbb-bc84-cfb758248189)

Overlaid are multiple rectangles, marking the usable range of the different tools on the machine head. Green marks the area which can be reached by the camera. The blue rectangle marks the area reachable by both nozzles and the red areas are only accessible by one of the nozzles.

Looking at his image, the issue should become rather clear: there is an area approximately 30 mm deep, spanning across the whole width in the back of the machine, where none of the nozzles can reach. This is wasted area of the 3rd staging plate and as this simple modification demonstrates how it is wasted for no reason.

## Proposed solution

The inaccessible area in the back of the machine can easily made useable by moving the staging plates 35 mm closer to the front of the machine. While 30 mm would be enough, the additional 5 mm cover potential variances for example in the assembly process of the machine. To retain all functionalities of the machine and to not break compatibility, the front feeder rail needs to move by the same amount for the feeders not to collide with the build plate. This in turn requires modifications to the front legs, as these define the position of this rail. This is the main content of this modification. The following image illustrates the new situation.

![Machine Table after](https://github.com/user-attachments/assets/a8398424-2f02-4b7d-996e-adfbfe844c60)

As can be seen in the image, the nozzles (blue and red) can now reach to the rear edge of the third staging plate and the front feeder pick window is still within reach of nozzles and camera. The nozzles can even reach as far as a fourth staging plate in the front. After all the y axis travel limit of 487 mm exceeds the length of four build plates, which are a total of 480 mm long. It is thus not only possible but also practical (see the picture in the top level README of this repo) to add a fourth staging plate in the front. 

Such a fourth staging plate can for example be used to support another full row of strip feeders. There are however some limitations to this practise. Because the front legs are in the way, a potential fourth staging plate needs a cut-out that is 20 mm wide and 46 mm long, to allow room for the front legs. It's also not possible to use the standard build plate foot, as it collides with the front feeder blades by merely 2 mm. Additionally, a potential fourth build plate needs cut-outs for as many LumenPnP Feeders as there are to be mounted onto the front feeder rail. The last limitation is that strip feeders mounted to this staging plate are only about half way through in the range of the camera. In order to use their full length, they need to be configured as tray feeders in OpenPnP, or something else that doesn't rely on vision. If during setup of the strip feeder the necessary care is taken, this is proven to not only work flawless but also considerably faster. 

There are multiple ways to accommodate the moved front feeder rail and staging plates. This solution is limited to only modifying the front legs, adjusting the least number of machine parts and slightly changing the configuration of OpenPnP. This severely limits the scope of the modification to a local optimum and leaves many more optimizations untouched. This is chosen to maximise the accessibility of the modification for as many users as possible. Other options would be to move the front feeder rail by a shorter distance because the frame of the LumenPnP Feeder could be made quite a bit shorter, as demonstrated in [this](https://github.com/jbussmann/PnP-mods/tree/draft_feeder-frame/LumenPnP%20Feeder/Feeder%20Frame) proposed modification. However this would break compatibility to the existing feeders as they are sold by Opulo. Additional optimization can be found by overhauling the design of the head assembly and parts of the gantry. This however is outside of the scope of this simple modification as it would involve printing many new parts, almost completely disassembling the machine and potentially even changing the controller firmware.

## Implementation

A pair of modified front feed are the core of this modification. They are remodeled from scratch, according to the original models, which turned out to be unworkable due to their complexity. The new model is stripped of all non-functional features and is thus much lighter in terms of the feature tree. It comes as individual stl-files, for those who just want to print it and as a FreeCAD multi-body part, for those who want to make further modifications. There are also two svg-files with the outline of the fourth staging plate, in case someone wants to have this too. One is a full staging plate and the other one is split, to accommodate 5 LumenPnP Feeder. Both feature the necessary cut-outs around the front feet.


A word of warning before diving in: this modification messes with the coordinate system, because it changes the homing fiducial position. All precise x and y coordinates become invalid and need to be checked and potentially updated. This applies to the tool changer positions but also to all feeder positions. Keep this in mind before you proceed and maybe save the following steps for a period of downtime.

- First of all you need to print the modified front feet.
- Remove the front feeder rail together with the angle-brackets from the machine.
- Use this rail to test fit all pockets and slots of the new 3D printed parts. Remove potential scrapes and bridging residues.
- Remove both of the existing front feet from the machine.
  - Remove the y axis striker.
  - Loosen both y axis idler pulleys and remove both idler pulley arms.
  - Now the feet themselves can be removed.
- Remove the angle-brackets form the front feeder rail. Due to the changed mounting of the rail, they will go somewhere else.
- Transfer all mounting elements form the old to the new 3D prints. Do the same with the feet extensions.
- On the left foot, don't forget the threaded insert for the y axis striker.
- With all that done, assembly can begin. This part is a bit cumbersome if you do a retrofit and didn't fully disassemble the machine.
  - Start by slotting both feet onto the front feeder rail.
  - Carfully slot the assembly onto the lower y axis rails.
  - Insert the top y axis rails into the feet and continuously push everything into place.
  - With everything firmly in place, tighten all the bolts.
  - Remount both y axis idler pulley arms and the idler pulleys.
  - Remount the y axis striker.
- As a last step mount the angle-brackets, now on top of the front feeder rail.

With all these steps done, the most difficult part is already done and now comes the fun part, which actually makes a difference: loosen all staging plates on the machine and realign them 75 mm away from the front feeder rail. You can do this like during the initial assembly by using the supplied jig. Now open OpenPnP and adjust the position of the homing fiducial, the bottom camera and every thing else that is bolted to the build/staging plate. Test if everything still works and enjoy the usable machine area that is now almost 10% larger compared to the standard triple build plate setup. Or a whopping 45% compared to the standard triple plate setup, in case you choose to add a fourth plate.

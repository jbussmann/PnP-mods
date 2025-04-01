# Y-Axis Optimisation

A modification optimising y-axis travel to increase the usable area of the machine in triple staging plate configuration by almost 10%. It involves replacing the front legs with newly printed ones, slightly rearranging the staging plates and updating the configuration of OpenPnP to reflect the changed geometry.

## Issue

The image below shows the machine in it's default configuration, drawn to scale. It shows the build plate as well as  the staging plate and both rows of LumenPnP Feeders. Additionally it shows in grey the optional 3rd staging plate in the back.

![Machine Table before](https://github.com/user-attachments/assets/1fbd882c-9a27-4277-84b3-134d62497cbe)

Overlaid are multiple rectangles, outlining the usable range of the different tools on the machine head. Green marks the area which can be reached by the camera. The blue rectangle marks the area reachable by both nozzles and the red areas are only accessible by one of the nozzles.

Looking at his image, the issue should become rather clear: there is an area approximately 30 mm deep, spanning across the whole width in the back of the machine, where none of the nozzles can reach. This is wasted area of the 3rd staging plate and as this simple modification demonstrates, it is wasted for no reason.

## Proposed Solution

The inaccessible area in the back of the machine can easily made useable by moving the staging plates 35 mm closer to the front of the machine. While 30 mm would be enough, the additional 5 mm cover potential variances for example in the assembly process of the machine. To retain all functionalities of the machine and to not break compatibility, the front feeder rail needs to move by the same amount for the feeders not to collide with the build plate. This in turn requires modifications to the front legs, as these define the position of this rail. This is the main content of this modification. The following image illustrates the new situation after the modification.

![Machine Table after](https://github.com/user-attachments/assets/eb8830d3-b8fd-4f46-b313-0ad17cf4e243)

As can be seen, the nozzles (blue and red) can now reach all the way to the rear edge of the third staging plate and the front feeder pick window is still within reach of nozzles and camera. The nozzles can even reach as far as a fourth staging plate in the front, added in grey. After all, the y-axis travel limit of 487 mm exceeds the length of four build plates, which are a total of 480 mm long. It is thus not only possible but also practical (see the picture in the top level README of this repo) to add a fourth staging plate in the front.

Such a fourth staging plate can for example be used to support another full row of strip feeders. There are however some limitations to this practise. Because the front legs are in the way, a potential fourth staging plate needs a cut-out that is 20 mm wide and 46 mm long, to allow room for the front legs. It's also not possible to use the standard build plate foot, as it collides with the front feeder blades by only a few millimetre. Modification of the foot or the mounting hole in the plate is needed. Additionally, a potential fourth build plate needs cut-outs for as many LumenPnP Feeders (or others) as there are to be mounted onto the front feeder rail. The last limitation is that strip feeders mounted to this staging plate are only about half way through in the range of the camera. In order to use their full length, they need to be configured as tray feeders in OpenPnP, or something else that doesn't rely on vision. If during setup of the strip feeders the necessary care is taken, this is proven to not only work flawless but also considerably faster.

There are multiple ways to accommodate the moved front feeder rail and staging plates. This solution is limited to only modifying the front legs, touching the least number of machine parts and changing the configuration of OpenPnP. Doing this severely limits the scope of the modification to a local optimum and leaves many more potential optimizations untouched. It is chosen to maximise the accessibility of the modification for as many users as possible. Other options would be to move the front feeder rail by a shorter distance because the frame of the LumenPnP Feeder could be made quite a bit shorter, as demonstrated in [this](https://github.com/jbussmann/PnP-mods/tree/draft_feeder-frame/LumenPnP%20Feeder/Feeder%20Frame) proposed modification. However, such a change would break compatibility to the existing feeders as they are sold by Opulo. Additional optimization can be found by overhauling the design of the head assembly and parts of the gantry. This however is outside of the scope of this simple modification as it would involve printing many new parts, almost completely disassembling the machine and potentially even changing the controller firmware.

## Implementation

The core of this modification is a pair of modified front feet. They are remodeled from scratch, according to the original models, which turned out to be unworkable due to their complexity. The new model is stripped of all non-functional features and is thus much lighter in terms of the feature tree. It comes as individual STL-files, for those who just want to print it and as a FreeCAD multi-body part, for those who want to make further modifications. There are also two SVG-files with the outline of a fourth staging plate, in case someone wants to have this too. One is a full staging plate and the other one is split, to accommodate 5 LumenPnP Feeders in the centre. Both feature the necessary cut-outs around the front feet and are intended to be used for cutting or milling. If the intention is to use PCBs, Opulo's [PCB design file](https://github.com/opulo-inc/lumenpnp/blob/main/pnp/pcb/staging-plate/staging-plate.kicad_pcb) is a better starting point.

A word of warning before diving in: doing this modification messes with the coordinate system, because it moves the homing fiducial. As a result, all precise x and y coordinates become invalid and need to be checked and potentially updated. This applies to the tool changer positions but also to all feeder positions. Keep this in mind before proceeding and maybe save the following steps for a period of machine downtime.

- First of all, print the modified front feet. They have the same requirements as the original parts, print settings can be found [here](https://docs.opulo.io/byop/mechanical-assembly/1-printing-parts/). 
- Remove the front feeder rail from the machine, together with the angle-brackets.
- Use this rail to test fit all pockets and slots of the new 3D printed parts. Remove potential scrapes and bridging residues.
- Remove both of the original front feet from the machine.
  - Remove the y-axis striker.
  - Loosen both y-axis idler pulleys and remove both idler pulley arms.
  - Now the feet themselves can be removed.
- Remove the angle-brackets form the front feeder rail. Due to the changed mounting of the rail, they will go somewhere else.
- Transfer all mounting elements form the original to the new 3D prints. Do the same with the feet extensions.
- On the left foot, don't forget the threaded insert for the y-axis striker.
- With all that done, assembly can begin. This part is a bit cumbersome if done as a retrofit instead of with a fully disassembled machine.
  - Start by slotting both feet onto the front feeder rail.
  - Carefully slot the assembly onto the lower y-axis rails.
  - Insert the top y-axis rails into the feet and continuously push everything into place.
  - With everything firmly in place, tighten all the bolts.
  - Remount both y-axis idler pulley arms and the idler pulleys.
  - Remount the y-axis striker.
- As a last step mount the angle-brackets, now on top of the front feeder rail.

With all these steps done, the most difficult part is already done and now comes the fun part, which actually makes a difference: loosen all staging plates on the machine and realign them 75 mm away from the front feeder rail. This is identical to the initial assembly and can be done by using the supplied jig.

Now open OpenPnP and adjust the position of the homing fiducial, the bottom camera and everything else that is bolted to the build/staging plate(s). This would be a good opportunity to update to the official release of OpenPnP 2.2 or even the most recent test build of OpenPnP 2.3 and try an improved machine.xml from [here](https://github.com/jbussmann/PnP-mods/tree/draft_machine-config/LumenPnP/Machine%20Config). Test and make sure that everything still works and enjoy the now almost 10% larger usable machine area, compared to the standard triple build plate setup. Or a whopping 45% compared to the standard triple plate setup, in case a fourth plate is added.

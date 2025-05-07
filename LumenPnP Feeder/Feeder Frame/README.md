# Feeder Frame: Draft

A modified frame for the LumenPnP Feeder. It improves the reliability of feeding parts on thick tape and comes in variants with guided tape discharge and/or much shorter overall length.

![03](https://github.com/user-attachments/assets/d209d2f5-38ad-44ff-aa37-b80cfd508c1d)

## Issue

The most severe issue, and also the most complained about apart from the price, with the LumenPnP Feeder is its inability to  to reliably feed thick paper tape commonly used for 0603 capacitors. The issue has two underlying contributors:
- Firmware: although he drive motor is powerful enough, it falls victim to a poor motor control strategy. The power supplied to the motor is reduced too soon and too aggressively before reaching the final position. Under this conditions, the motor is unable to overcome the high friction of thick paper tape and therefore unable to properly drive the tape. Changing this would involve recompiling the firmware.
- Hardware: The interface between the drive wheel and the tape is designed unfavourably. The tape is bent partway around the drive wheel which causes the drive wheel sprockets to get stuck in the case of thick tape. This increased friction leads to unnecessarily high torque requirements for the drive motor. The easiest of several ways of solving this only requires minimal changes to the 3D printed feeder frame.

Another minor issue with the feeder frame is the positioning of the pick window relative to the drive wheel with the pick window being significantly behind the drive wheel axis. This not only leads to unnecessary parts loss when loading the tape but also to potential variance in the positioning of the tape.

## Proposed Solution

This modification focuses on improving the mechanical aspects of the feeder frame because for many people this is easier than to change the firmware. In essence, reducing the friction between the drive wheel and the tape comes down to reducing the angle/distance the the tape is bent along the drive wheel or changing the drive wheel geometry. Since the former is more accessible, as it only requires 3D printing a new frame, this is what will be discussed in the following paragraphs.

The simplest way of fixing the issue is to simply reduce the output bending angle, like Opulo has in the meantime implemented it according to their description [here](https://www.opulo.io/blogs/news/march-2025-opulo-update). This is in fact so simple that it even can be applied to existing old feeder frames, by simply cutting away a small part of the frame right below the fiducial PCB. It works great but unfortunately, it creates another issue: with the shallower exit angle, there is a potential risk for the tape colliding with the staging plate before slipping under the plate. This can happen smoothly but it can also happen with a jolt, in which case it might disrupt uncovered passive feeders on the staging plate and send their parts flying.

A more thorough way of fixing the issue is to completely separate the drive wheel interface from the exit bend in the tape by moving the drive wheel to the back and/or the exit bend to the back. This first and foremost reduces the friction at the drive wheel interface, allows the feeder to much more easily handle thick tape and also avoids the secondary issue of potential collisions between the exiting tape and tha staging plate. Additionally, moving the drive wheel 7mm further back has the nice advantage of aligning it with the pick window and therefore improving also on the last issue initially mentioned.

All these changes retain full compatibility to the rest of the machine. However, the LumenPnP Feeder suffers from very inefficient packaging, is therefore much bigger then needed and can be shortened significantly. Fot that reason, this modification also contains a version of the feeder frame that is roughly 15mm shorter then the original version with the pick window 13mm further back. Compared to the original feeder, the drive train can be moved a whole 20mm further to the back. However, the initial modification already uses up 7mm of this by aligning the drive wheel with the pick window.

Repositioning the pick window like this unfortunately breaks some compatibility. While there is no issues with the front feeder row, when mounted onto the back feeder rail, the pick window is now outside the range of motion of the nozzles. This can easily be fixed by slightly moving the back feeder rail to the front of the machine (by how much?). Justifying this change are also multiple advantages. The smaller feeder takes less material to print and less space to store. Much more importantly, the shorter feeder allows to regain parts of the lost space on the machine table, as discussed in [this](https://github.com/jbussmann/PnP-mods/tree/main/LumenPnP/Y-Axis) modification but with much less work. The shorter feeder allows the distance between front feeder rail and the build plate to be reduced from 75mm to 60mm and thus regaining half of the inaccessible area in the back of the machine if a third staging plate is installed. The following image shows this situation, analogous to the linked modification.


<!-- For reasons I will write about in much greater detail in the future, the further the tape is bent along the drive wheel, the harder it is to drive it. When I used the feeder in it's original configuration, it always required multiple attempts to reach the final feed position. After feeding maybe 5 components, the feeder would not reach the position within its 3 attempts it is allowed to take and it would disable and detach from the machine. See following picture for reference.
![01](https://github.com/user-attachments/assets/37c62274-e2bb-402c-970f-b0638493c2f1)

The first hacky attempt to solve this, was to cut the part right below where the feeder fiducial sits. This allows the tape to exit the feeder at a much shallower angle with the bending angle around the drive wheel being smaller and therefore also reducing the required force to drive the tape. This improved the situation to the point that the machine sometimes could run unattended. Each feed still took 2-3 attempts but only every 100 components or so, this was not sufficient and the feeder would again detach. See following picture for reference.
![02](https://github.com/user-attachments/assets/3ba63317-228c-4790-9032-117d3f9dcbe2)

Then I finally redid the whole feeder frame. I had to rebuild the whole model from scratch because my computer is unable to process the original model in a useful way. Below is the first attempt, try-all-at-once style.
![03](https://github.com/user-attachments/assets/d209d2f5-38ad-44ff-aa37-b80cfd508c1d)
- The primary goal was to not bend the tape at all across the drive wheel, in an attempt to minimize the required drive force.
- Because the feeder is awkwardly inefficiently packed, I moved the drive motor a whole 20mm closer to the PCB to test if everything still fits.
- The average user will not benefit from a more compact feeder design, thus I used the freed up space to fold back the tape so it doesn't create a mess under the machine table.
- Additionally I moved the pick window vertically above the drive wheel axis, where it belongs in my opinion. I also made it a bit shorter.

I don't have a real job at hand to test right now, so I just loaded the reel that caused problems before and picked maybe 10-20 components by discarding them afterwards. I think this is identical to a real pick operation during a job, but I'm not 100% sure. Either way, all those feed operations completed in the first try, even though bending the tape along the exit certainly posed additional resistance (I planned to cut the exit bend, in case it wouldn't work). Thus I call this a (preliminary) success, indicating where this will lead. -->

## Implementation

Printers with good bridging performance can easily print the model without support material. If this is not the case, add support material as necessary. 


ToDo:
- check exact back feeder rail position
- shorter version: peel guide, number, 12mm version
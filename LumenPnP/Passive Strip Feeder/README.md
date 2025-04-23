# Passive Strip Feeder

A much improved version of the popular Menlu strip feeder, originally designed by ERIK3DP. It allows the LumenPnP to easily use small parts and thin plastic tape without the headache of parts jumping all over tha place. 

## Issue

The strip feeders provided by Opulo to accompany the LumenPnP are of a very simplistic design. This is a compromise and leads to limitations in their application. The main issue of these stock feeders is their inability to fixate thin tape in the vertical direction. Their fixed geometry works adequately with thick tape but because they have no moving parts to compensate for different tape thicknesses, these feeders are especially problematic for parts in thin tapes like 0402 components and plastic tapes. It is almost impossible to use such parts as simply touching the tape can send all the parts flying that are no more protected by the cover film. 

## Proposed Solution

To solve the issue of loose tapes, the feeder has to vertically fixate the tape. One simple way to do this is by a spring loaded mechanism beneath the tape, pushing it upwards. The Menlu strip feeder by [ERIK3DP](https://www.printables.com/model/885928-menlu-strip-feeder-8mm12mm-for-lumenpnp) is a very popular example of such a feeder system. The OpMenlu strip feeder by [ruudwes](https://www.printables.com/model/1147285-opmenlu-stripfeeder-for-the-lumenpnp) is based on the original Menlu feeder but in many ways improved and further adapted to the LumenPnP. 

The OpMenlu strip feeder system consists of two parts, a stationary base, bolted to the machine table, as well as a movable slider. Although this feeder has a lot of potential, it still has several shortcomings. When asked to improve on these, the author of the OpMenlu feeder deemed some of the suggested improvements unnecessary or impossible to solve and did only offer to share the parametric model, when it was already too late.

As a consequence, the feeder presented here is completely remodeled from scratch. It is heavily inspired by the many good ideas of the Menlu and OpMenlu designs but is at the same time in many aspects massively improved:

- The tape's surface is now 10 mm above the staging plate, where the top camera's focal plane, the PCBs and all other feeders are. This is more than 1 mm lower than before.
- The base has the full array of mounting holes available for maximum flexibility.
- All mounting holes are easily accessible from above without the need to remove the slider. This is especially useful if multiple sliders are mounted in a row, which the design is intended to be used for.
- The slider wall supporting the sprocket holes is now rectangular and much thicker at the point where it connects to the slider body. This makes it much less likely to break off e.g. when removing potential support material.
- The slider wall opposite of the sprocket holes on the other hand is now thinner. This is to accommodate tapes with very large components and consequently very thin tape edges.
- The 8 mm feeders are available in compact arrays of 4 and 10 rows with a pitch of 10 mm. They occupy the same area as 3 or 7 rows of the standard design with 15 mm row pitch would, thus making this design up to over 40% more space efficient.
- This modification also contains a wider 12 mm version of the same design, as these wider tapes suffer from the same issue.
- The overall design is stripped of all unnecessary features and improved for 3D printing.

As this comprehensive list demonstrates, all shortcomings of the OpMenlu design were easily solvable. At the same time the mushroom style caps, used to guide the cover tape, were deemed only marginally useful and were therefore removed in the process of making the design more compact. 

## Implementation

There are subfolders for the 8 and 12 mm designs, each containing FreeCAD models of both the base of the feeder and its corresponding slider. Additionally there are STL-files for 3D printing of the slider and the base, latter of which in different numbers of rows. The prints should turn out well even when printed with 0.2 mm layers. There are however two critical areas of the model:

- The slider requires bridging at a height of 2.5 mm. With the appropriate settings, this can easily be printed without support material. If in doubt, enable support.
- There is a ramp. On the slider it's between 4.5 and 6.5 mm height and on the base it's between 3.0 and 3.8 mm. Printing this with 0.2 mm will be very rough and has the potential to make the mechanism unusable. One way to solve this is to print either the base or the slider (one of both is enough) with 0.10 to 0.12 mm layer height. A more elegant solution is to use a layer height modifier (as supported e.g. by the Prusa slicer and Bambu Studio) to reduce the layer height to between 0.10 and 0.12 mm only in the range where this ramp is. Again, doing this on only one of both parts should be enough.

After printing the parts, test fit the slider into the base. If it gets stuck, cut or file away whatever excess material there is. If the fit is good, use a suitable rubber band/ring to mount the parts together.

In its shortest position, the required rubber band is roughly 32 mm long (10 mm diameter), while in its longest position it's roughly 56 mm long (18 mm diameter). To exert an uniform force over the the whole range, the rubber needs to be shorter than the shortest position and be able to stretch to at least 3 times its original length. A thin and soft band with around 6 mm diameter works well. Springs might work as well but are not tested. When needed, adapt the model and move the pins to fit the requirements.


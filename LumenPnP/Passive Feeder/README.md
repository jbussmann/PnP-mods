# Passive Strip Feeder

A much improved version of the popular Menlu strip feeder, originally designed by ERIK3DP. It allows the LumenPnP to easily use small parts and plastic tape without the headache of parts jumping all over tha place. 

## Issue

The strip feeders provided by Opulo to accompany the LumenPnP are of a very simplistic design. This this is a compromise and leads to limitations in their application. The main issue of the stock feeders is their inability to fixate the tape in the vertical direction because they have no moving parts but still need to work with different tape thicknesses. Therefore there feeders are especially problematic for for parts in thin tapes like 0402 components and plastic tapes. It is almost impossible to use such parts as simply touching the tape can send all parts flying that are not protected by the cover film. 

## Proposed Solution

To solve the issue of loose tapes, the feeder has to vertically fixate the tape. One simple way to do this is a spring loaded mechanism beneath the tape, pushing it upwards. The Menlu strip feeder by [ERIK3DP](https://www.printables.com/model/885928-menlu-strip-feeder-8mm12mm-for-lumenpnp) is a very popular example of such a feeder system. The OpMenlu strip feeder by [ruudwes](https://www.printables.com/model/1147285-opmenlu-stripfeeder-for-the-lumenpnp) is based on the original Menlu feeder but in many ways improved and further adapted to the LumenPnP. Although the OpMenlu feeder has a lot of potential, it still has several shortcomings:

- The tape surface is more than 1 mm above the PCB surface and the other feeders. This means the parts are slightly out of focus and when setting up the feeders, one needs to constantly be aware that this feeder is higher up than everything else on the machine. Otherwise the nozzle tip can easily bunch through the tape.
- There is only a very limited amount of screw holes available on the base, which makes mounting to the build plate a bit cumbersome. Many of them are additionally made impossible to access by the slider covering them.
- Depending on which holes are used, the feeder can only be mounted to or removed from the machine when the sliders are removed. This is especially problematic, when the feeders are chained lengthwise (which they are intended to be) because then, the slider can only be removed on the last feeder in the row.
- The wall supporting the sprocket holes is too thin at its base and can easily break off when removing potential support material.
- On the other hand, the wall opposite of the sprocket holes is too thick to be working with large components.
- The design only exist for 8 mm tape, but 12 mm tape suffers from the same issue.
- The feeder comes in a handy tripple tape array spanning 3 rows of holes. With a pitch of 15 mm it occupies a 45 mm wide slot on the build plate, enough room for 4 tapes with a pitch of 10 mm. 
- Overall the design has several unnecessary features, is at the same time missing some more important features and has room to be optimized for 3D printing.

When asked to improve on these shortcomings of the design, the author of the OpMenlu feeder deemed the suggested improvements unnecessary or impossible and did not respond to a request to share the parametric model.

As a consequence, this modification is completely remodeled from scratch. It is heavily inspired by the many good ideas of the Menlu and OpMenlu designs but at the same time massively improved in all the above mentioned issues. As it turned out, all of them were easily solvable on not even remotely impossible to solve. 

## Implementation

There are subfolder for the 8 and 12 mm designs, each containing FreeCAD models of both the base and the slider. Additionally there are STL-files for 3D printing of the slider and the base in different array lengths. The prints should turn out well even when printed with 0.2 mm layers. There are two critical areas of the model:

- The slider requires bridging at a height of 2.5 mm. With the appropriate settings, this can easily be printed without support material. If in case of doubt, enable support.
- There is a ramp. On the slider it's between 4.5 and 6.5 mm and on the base it's 3.0 and 3.8 mm. Printing this with 0.2 mm will be very rough and potentially unusable. One way to solve this is to print either the base or the slider (one of both is enough) with 0.10 to 0.12 mm. A more elegant solution is to use a layer height modifier (as supported e.g. by the Prusa slicer and Bambu Studio) to reduce the layer height to between 0.10 and 0.12 mm only in the range where this ramp is. Again, doing this on only one of both parts should be enough.

After printing the parts, test fit the slider into the base. If it gets stuck, file away whatever excess material there is. If the fit is good, use a suitable rubber band/ring to mount the parts together.

In its shortest position, the required rubber band is roughly 32 mm long (10 mm diameter), while in its longest position it's roughly 56 mm long (18 mm diameter). To exert an uniform force over the the whole range, the rubber needs to be shorter than the shortest position and be able to stretch to at least 3 times its original length. A thin and soft band with around 6 mm diameter works well. Springs might work as well but are not tested. When needed, adapt the model and move the pins to fit the requirements.


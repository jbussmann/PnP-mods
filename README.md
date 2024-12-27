# PnP-mods

This repository is about my awesome little [LumenPnP](https://www.opulo.io/products/lumenpnp) desktop pick and place machine. Well actually, it belongs to my employer because I use it at work. I ordered the machine around a month after the release of v4 in fall 2024 because we were running out of time with a development project. It became increasingly apparent that no contract manufacturer would be able to assemble the boards we needed in the time we had left between end of development and start of testing. Also hand assembly was no option due to the high complexity of 60 PCBs with 240 placements and another 60 PCBs with 120 placements, with more than half of it being 0402 components. This is when I decided to take the plunge on desktop pick and place, in a slightly desperate attempt to make the deadline. The LumenPnP gave us a fighting chance to do so.

![LumenPnP](https://github.com/user-attachments/assets/8972377d-7065-49b8-a308-e6e1bccb531e)

This potato cam picture shows what I was working with at this time. During the roughly 10 days of machine time it took me to assemble all those boards, I not only learned a lot about the machine and [OpenPnP](https://openpnp.github.io), its accompanying control software, but I also run into several limitations and issues. Some are inherent to the approach of both hardware and software and therefore deeply baked into the design. Others are more like oversights or specific to my setup because as can be seen in the picture, space is one of the most limiting factor. The latter of those limitations and issues I tried and still am trying to improve on. This repository is a collection of my findings and my attempted improvements.

Many things are still work in progress or even just concepts I might or might not try at some point. Following are the topics I intend to address in the future.

### LumenPnP:
- optimize usable range of motion in the y-axis
- shrink nozzle rack
- improve passive strip feeders for 0402 components

### LumenPnP Feeder:
- improve ability to feed 1mm paper tape
- improve reliability with 0402 components
- improve packaging

### OpenPnP:
- simplify setting up a new job
- macro keyboard for "eyes off screen" machine control
- improved job planning and execution

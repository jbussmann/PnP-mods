# Feeder Frame: Draft

This is a very preliminary discussion of one of the issues I have with the LumenPnP feeders and the first attempt at solving it. I wouldn't normally share this but curious people have asked. :)

One of the issues of the LumenPnP Fedders (probably the most severe one) is their inability to reliably feed 1 mm thick paper tape commonly used for 0603 capacitors. The issue has two underlaying contributors:
- The drive motor, although powerful enough, falls victim to a poor motor control strategy and is therefore unable to properly drive the tape. For me this is the harder problem and something I might tackle later on, if Opulo hasn't solved it until then.
- The interface between the drive wheel and the tape is designed unfavourably. Solving this only requires 3D printing and is what I will andress here.

For reasons I will write about in much grater detail in the future, the further the tape is bent along the drive wheel, the harder it is to drive it. When I used the feeder in it's original configuration, it always needed multiple attempts to reach the final position. After feeder maybe 5 components, the feeder would not reach the position within its 3 attempts it is allowed to take and it was disabled and detached from the machine. See following picture for reference.
![01](https://github.com/user-attachments/assets/37c62274-e2bb-402c-970f-b0638493c2f1)

The first hacky attempt to solve this, was to cut the part right below where the feeder fiducial sits. This allows the tape to exit the feeder at a much shallower angle with the bending angle around the drive wheel being smaller and therefore also reducing the required force to drive the tape. This improved the situation to the point that the machine sometimes could run unattended. Each feed still took 2-3 attempts but only every 100 components or so, this was not sufficient and the feeder would again detach. See following picture for reference.
![02](https://github.com/user-attachments/assets/3ba63317-228c-4790-9032-117d3f9dcbe2)

Then I finally redid the whole feeder frame (I had to rebuild the whole model from scratch because my computer is unable to process the original model in a useful way. Below is the first attempt, try-all-at-once style.
![03](https://github.com/user-attachments/assets/d209d2f5-38ad-44ff-aa37-b80cfd508c1d)
- The primary goal was to not bend the tape at all across the drive wheel, in an attempt to minimize the required drive force.
- Because the feeder is awkwardly inefficiently packed, I moved the drive motor a whole 20mm closer to the PCB to test it everything still fits.
- The average user will not benefit from a more compact feeder design, thus I used the freed up space to fold back the tape so it doesn't create a mess under the machine table.
- Additionally I moved the pick window vertically above the drive wheel axis, where it belongs in my opinion. I also made it a bit shorter.

I don't have a real job at hand to test right now, so I just loaded the reel that caused problems before and picked maybe 10-20 components by discarding them afterwards. I think this is identical to a real pick operation during a job, but I'm not 100% sure. Either way, all those feed operations completed in the first try, even though bending the tape along the exit certainly posed additional resistance (I planned to cut the exit bend, in case it wouldn't work). Thus I call this a (preliminary) success, indicating where this will lead.

The attached model is what you see here. It is a quickly hacked together mess, nowhere close to being finished or adequately tested. Use at your own risk. Feedback is highly appreciated.

I will merge this into the main branch as soon as I think it has matured to the point where I think it is safe for everyone to use. 

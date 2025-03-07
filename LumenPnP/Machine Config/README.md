# Machine Config: Draft

My attempt at a clean machine.xml for the LumenPnP, created from scratch and containing only settings applicable to all machines. It is intended to be used in conjunction with OpenPnP's Issues & Solutions and allowes users to skip the Welcome, Connect, Basics and Kinematics milestones and start right off targeting the Vision and Calibration milestones. This is still incomplete and untested, use at your own risk. Feedback is highly appreciated.

## Issue

There are maninly two ways to configure a LumenPnP:
- Starting from scratch and using Issues & Solutions  
This is what the developers of OpenPnP recommend. It is clean but also a lot of work. Additionally, it is unneccecary work because a lot of the resulting configuration is common to all LumenPnPs and can therefore be summarised in a machine.xml template. 

- Following the instrucions provided by Opulo
This provides a preconfigured machine.xml template however it is a messy one. It contains a lot of old and deprecated configuration fragments, as well as configuration data that is specific to the machine the template was originally created on. Furthermore, Opulo's instructions do all the calibration by hand. This is cumbersome, labor intensive and in many instances, there is a hands-off calibration procedure available which achieves the same goal, just faster and more accurate.

Both approaches are far from ideal and provide a suboptimal user experience.

## Proposed solution

To privide users with the best possible experience this solution provides a configuration file, purpose built from scratch. It aims at making the user calibration as short and smooth as possible while at the same time leveraging as many capabilities as possible of both the machine as well as the software. Starting from scratch, this configuration file does several things different than Opulo does in their own machine.xml
- Either solve or dismiss all solutions in Issues & Solutions until targeting the vision milestone.
- Clean up all gcode commands and make them match the suggestions by Issues & Solutions.
- Add calibration data to the nozzle tips themselves instead of hardcoding it in the pipeline stages.
- Reset all vision pipelines to default.
- Change from tool path to mederated acceleration and allow seperate tuning of all axes.

This allows the calibration procedure to improve considerably:
- Use of a one click solution to determine homing fiducial location, determine top camera orientation, roation angle and unit per pixle.
- Use of a one click solution to determine bottom camera location, orientation, ratation angle and unit per pixle.
- Use of advanced nozzle offset calibration solution to easily determine the nozzle offset as precise as the machine's motion system allows.
- Use of the built in nozzle tip runout calibration which leverages linked vision stages.
- Use of adaptive camera settling to minimize settling time.
- Use of nozzle tip background calibration to quickly and easily configure the camera exposure.
- Optional use of of the backlash calibration solution which provides a comprehensive reflection of the state of the motion system.

## Limitations

This config is created on and for OpenPnP 2.2 which was built in February 2025. It is also tested to work on newer builds but it is unlikely to work with older builds. This is due to a limitation in the xml parser, which is unable to handle elements in the config file, if they didn't exist in older versions of OpenPnP.

Unfortunately the OpenPnP 2.2 release was before this configuration file was finalized. Therefore, not all bugs that came up during the creation of the config could be fixed in time. At least one remains in the  2.2 release and was only fixed later on:

- The LumenPnP has no secondary fiducial, therefore the associated calibaration in Issues & solutions is to be dismissed. Due to a bug, dismissing this solution through the UI is impossible and was therefore dismissed by manually editing the configuration file. Due to the same bug, users are also unable to reopen this solution, in case they wish to use a custom made secondary fuducial. To reopen this solution either update to a newer build of OpenPnP or manuall remove the line `<string>831b760f63cd9d1b93a457157a4f8c366aa0cf33</string>` from the config file under `dismissed-solutions`.
- Camera settings getting lost.

## Implementation

There will be a video about how to progress through the few steps from the state that the config file provides to picking and placing the first parts. For those who don't want to wait or prefer text based instructions, here is a preliminary list of the steps that remain to be completed.

While targeting milestone vision:
- Accept the enable and home machine solution  
Relevant Opulo docs: [Homing Fiducial](https://docs.opulo.io/openpnp/calibration/4-homing-fiducial/)
- Manually load nozzle tips NT045 and NT24  
Relevant Opulo docs: [Mounting Nozzle Tips](https://docs.opulo.io/openpnp/calibration/5-mm-per-pixel/#mounting-nozzle-tips)
- Manually test the vacuum system and setup the thresholds  
Relevant Opulo docs: [Vacuum Part Detection](https://docs.opulo.io/openpnp/calibration/10-vacuum-sensor/)
- Accept the set primary fiducial solution, use a feature diameter of 92px  
Relevant Opulo docs: [Setting Homing Fiducial Location](https://docs.opulo.io/openpnp/calibration/4-homing-fiducial/#setting-homing-fiducial-location) and [Top Camera Calibration](https://docs.opulo.io/openpnp/calibration/5-mm-per-pixel/#top-camera-calibration)
- Accept the enable visual homing solution  
Relevant Opulo docs: [Test Fiducial Homing](https://docs.opulo.io/openpnp/calibration/4-homing-fiducial/#test-fiducial-homing)
- Accept the use adaptive settling solution for the top camera
- Accept the nozzle N1 offset for primary fiducial solution
- Accept the nozzle N2 offset for primary fiducial solution  
Relevant Opulo docs: [Nozzle Offset](https://docs.opulo.io/openpnp/calibration/6-nozzle-offset/)
- Accept the bottom camera initial calibration, use feature diameter of 12px and disable auto focus  
Relevant Opulo docs: [Bottom Camera Position](https://docs.opulo.io/openpnp/calibration/7-bottom-camera-position/) and [Bottom Camera Calibration](https://docs.opulo.io/openpnp/calibration/5-mm-per-pixel/#bottom-camera-calibration)
- Accept the use adaptive settling solution for the bottom camera  
- Accept the milestone vision

While targeting milestone calibration:
- Dismiss or accept the backlash compensation for x and y axes
- Manually set the primary fiducial location to where the hole punch is
- Accept the N1 precise nozzle offset solution
- Manually readjust primary fiducial location if necessary
- Accept the N2 precise nozzle offset solution
- Manually reset the primary fiducial location to homing fiducial
- Manually enable nozzle tip calibration on all six nozzle tips
- Accept nozzle tip background calibration for all loaded nozzle tips
- Acceept the milestone calibration

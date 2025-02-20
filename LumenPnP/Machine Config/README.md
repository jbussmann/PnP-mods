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
- 

## Implementation

There will be a video about how to progress through the few steps from the state that the config file provides to picking and placing the first parts.

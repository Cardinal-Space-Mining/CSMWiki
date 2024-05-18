## Overview
The HTC Vive tracker can estimate its pose relative to mounted base stations with known positions.
### Base Stations
The system is comprised of base station and trackers.  Base stations are statically mounted in known positions and emit continuous IR laser sweeps and timing pulses.
### Trackers
Trackers are covered in photo-receptors that monitor base station sweeps.  By measuring the timing between photo-receptor activation trackers can multilaterate their position relative to the original base station with near-millimeter accuracy.
## SteamVR vs Libsurvive
The original Vive system used an open source reverse implementation of the Vive trackers called [Libsurvive](https://github.com/cntools/libsurvive).  However, library accuracy is low, especially with Gen2 Lighthouse tracking systems, and development has stalled.
As a result, we have transitioned to using the official SteamVR runtime, which provides much more accurate calibration and tracking.
## Tech Stack
Using the sensors independently of the headset requires a pretty monstrous tech stack, designed with the following components:
```
+----------------+
|  Triad OpenVR  |
+----------------+
        |
        v
+----------------+
|    PyOpenVR    |
+----------------+
        |
        v
+----------------+
| Monado Runtime |
+----------------+
        |
        v
+----------------+
|    SteamVR     |
+----------------+
```
### SteamVR
Provides the actual VR tracker interface and tracking functionality.  Installable using Steam.
### Monado Runtime
An OpenXR runtime that enables communication with the SteamVR runtime on Linux.  Install on Ubuntu using packages `libopenxr1-monado` and `monado-service`.
### PyOpenVR
A now abandoned python library that provides python bindings for OpenVR functions.  Still works for now, but investigation into [PyOpenXR](https://github.com/cmbruns/pyopenxr).
### Triad OpenVR
A python library that wraps OpenVR functions into a usable interface.  Provides functionality for:
- Identifying trackers and lighthouses by serial number
- Retrieving tracker pose as a matrix or quaternion
- Identifying active lighthouses and their poses
## Limitations
### Calibration
The biggest problem with this stack is that lighthouses and trackers are projected into an essentially random work frame every run.  On startup, an arbitrary lighthouse's pose is used as origin position and rotation, after which all other tracker and lighthouse positions are measured in that reference frame.
As such, initial pose of at least one lighthouse must be known in order to transform everything into the correct frame.  The current implementation over-complicates this by using Iterative Closest Point between the measure world frame and Vive frame to estimate the initial pose offset.
### Daylight
Vive uses IR lasers, meaning they are susceptible to interference from sunlight.  As such, they are for indoor localization only and any outdoor testing must be done at night.
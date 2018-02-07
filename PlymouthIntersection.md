# <font color='blue'>Plymouth Intersection Data Nugget Documentation</font>

## Summary
This document describes the Plymouth Intersection dataset that is available on Flux through Globus Connect. 
This data nugget is a compilation of 4 datasets:
1. Transmitted BSMs
2. Received BSMs (V2V interaction)
3. RSE (V2I interaction)
4. Forward Video

## Event Identification
Events were identified according to the following constraints:  
1. Vehicle 1 must enter and stop at a Plymouth road intersection (buffer zone of 50m radius)
2. Vehicle 1 must have forward video capability
3. Vehicle 1 must be the leading car in its lane
4. Vehicle 2 must also enter the intersection at the same time
5. There must be V2V communication between the vehicles 1 and 2

Events begin approximately when vehicle 1 stops at intersection.  
Events end approximately when vehicle 1 finishes passing through intersection.

This data nuggets contains **51** events identified at Plymouth road Intersections.

## Folder/File Naming Convention
Files are organized into folders based on a single event.  
The top level folder(s) is named `TripStart/datanuggets/PlymouthIntersections/intersectionEvents`.  
The folder name format is `event_rseId_vehicle1Id_vehicle1TripId_StartTime_EndTime`.  
For example, folder "event_18010_10155_482_2103_3065" equates to:

Name|Id|Units
---|---|---
RSE|18010|None
Vehicle 1|10155|None
Vehicle 1 Trip|482|None
Start Time|2103|centiseconds since DAS started
End Time|3065|centiseconds since DAS started

There are 4 files within the event folder that follow a similar convention.  
`Forward_18010_10155_482_2103_3065.avi`  
`bsm_18010_10155_482_2103_3065_10597_2732704.csv`  
`rse_18010_10155_482_2103_3065_10597_2732704.csv`  
`rxbsm_18010_10155_482_2103_3065_10597_2732704.csv`

The *bsm, rse, rxbsm* files have two additional numbers appended to the filename. They indicate `vehicle2Id` and `vehicle2TripId`.
For example, file "bsm_18010_10155_482_2103_3065_10597_2732704.csv" equates to:

Name|Id|Units
---|---|---
Type of File|BSM|None
RSE|18010|None
Vehicle 1|10155|None
Vehicle 1 Trip|482|None
Start Time|2103|centiseconds since DAS started
End Time|3065|centiseconds since DAS started
Vehicle 2|10597|None
Vehicle 2 Trip|2732704|None

## Data Size
The total size of the dataset is about 80 MB (uncompressed).

## Data Format
The data format is the same as it is for the BSM, RSE, BSMRx dataset since it is extracted from there.

## Video Information
The AVIs use the DivX codec. If you are having trouble playing the video, I was able to get it working with the [VLC media player](https://www.videolan.org/index.html)

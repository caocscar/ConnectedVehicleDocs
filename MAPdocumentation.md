# MAP Documentation for Connected Vehicle Dataset

## Summary
This document describes the UMTRI MAP dataset that is available on Flux through Globus Connect. The data represents the MAP messages used to provide intersection and roadway lane geometry data for one or more locations. Almost all roadway geometry information as well as roadway attributes (such as where a do not block region exists, or what maneuvers are legally allowed at a given point) is contained in the “generic lane” details of this message.  MAP messages are used in intersections to number and describe lane level details of each lane, while the SPAT message provides the current state of each signal head controlling the ability to stop/pass a given lane. 

Since MAP messages do not change (since intersection geometry is constant barring significant construction), the dataset only contains a single instance of that message to reduce redundancy.

The table represents the MAP messages available that are transmitted by Roadside Equipment (RSE) devices in the Plymouth Road corridor.

RxDevice|Location|MapMD|AEB|Lane|Node
---|---|:---:|:---:|:---:|:---:
18010|Plymouth and Barton|Yes|No|No|No
18012|Plymouth and Traverwood|Yes|Yes|Yes|Yes
18013|Plymouth and Nixon|Yes|Yes|Yes|Yes
18014|Plymouth and Huron Parkway|Yes|Yes|Yes|Yes
18015|Plymouth and Green|Yes|Yes|Yes|Yes
18022|Plymouth and Murfin|Yes|No|No|No

## Data Filtering
No filtering has been done to MAP messages. 

## File Content Description
Each file is comma delimited. Files do have column headers.

## Data Size
The total size of the dataset is 8 KB.

## Variables
Here is the variable definitions for the four MAP type files.

### MapMD
The **RxDevice** column represents the primary key for the dataset.

Column Number|Name|Description|Units
:---:|---|---|---
1|RxDevice|device Id of the RSE|none  
2|FileId|unique number assigned to each file; not the same FileId in the BSM dataset|none
3|TxDevice|another RSE Device Id|none
4|Gentime|number of microseconds since Jan 1, 2004 (UTC +00:00)|microseconds  
5|MsgCount|MAP message count (restarts with new pcap file)|none
6|FrameOffset|
7|FrameSize|
8|MapRelOffset|
9|MapPayLoad|
10|GenTimeRelOffset|
11|Version|
12|MessageAttr|
13|Latitude|y-reference point of intersection|degrees
14|Longitude|x-reference point of intersection|degrees
15|Elevation|z-reference point of intersection|
16|AEBCount||

### AEB (Approach/Egress/Barrier)
The **RxDevice** column represents the primary key for the dataset.

Column Number|Name|Description|Units
:---:|---|---|---
1|RxDevice|device Id of the RSE|none  
2|FileId|unique number assigned to each file; not the same FileId in the BSM dataset|none
3|TxDevice|another RSE Device Id|none
4|MsgCount|MAP message count (restarts with new pcap file)|none
5|AEBCount||
6|AEBType||
7|LaneCount|Number of lanes in intersection|lanes
8|PriPreLoad||

### Lane
The **RxDevice** and **Lane** columns represents the composite primary keys for the dataset.

Column Number|Name|Description|Units
:---:|---|---|---
1|RxDevice|device Id of the RSE|none  
2|FileId|unique number assigned to each file; not the same FileId in the BSM dataset|none
3|TxDevice|another RSE Device Id|none
4|MsgCount|MAP message count (restarts with new pcap file)|none
5|AEB|
6|Lane|lane number|none
7|LaneType*|1-motorized vehicle lane, 2-computed lane, 3-pedestrian lane, 4-special purpose lane|none
8|LaneId|lane Number (same as column 6)|none
9|LaneAttr*|unsigned 16-bit integer describing the lane attributes|none
10|BarrierAttr*|unsigned 16-bit integer describing the barrier attributes|none
11|Width|lane or barrier width|cm
12|ConnLaneId|lane id of a previously defined lane to which this lane connects|lane
13|ConnCode*|unsigned 8-bit integer describing the maneuver code|none
14|RefLaneId|lane id of reference lane that a computed lane parallels|none
15|RefLatOffset|signed 16-bit integer describing the lateral offset of reference lane|cm
16|NodeLoad|
17|NodeAttr|unsigned 8-bit integer describing the node attributes|none
18|NodeNumOfPts|Number of nodes in each lane|nodes

\*Enumerated values for these columns can be found in the reference documentation mentioned below. 

### Node
The **RxDevice**, **Lane**, and **Node** columns represents the composite primary keys for the dataset.

Column Number|Name|Description|Units
:---:|---|---|---
1|RxDevice|device Id of the RSE|none  
2|FileId|unique number assigned to each file; not the same FileId in the BSM dataset|none
3|TxDevice|another RSE Device Id|none
4|MsgCount|MAP message count (restarts with new pcap file)|none
5|AEB|
6|Lane|lane id|none
7|Node|node id|none
8|NodeEastOff|node eastern offset relative to the intersection reference point|cm
9|NodeNorthOff|node northern offset relative to the intersection reference point|cm
10|NodeEleOff|node elevation offset relative to the intersection reference point|cm
11|NodeWidth|lane width at node location|cm

**Note**: Missing descriptions mean I did not find a good reference in the documentation to explain the column.

## Reference
Variable definitions were taken from the Word document `J2735_SPATblob_MAPblob_RevC_20120217.docx` in the `TripStart/map/documentation` folder.

## Coordinate Reference System
GPS coordinates are in WGS84 or EPSG:4326

# MAP Documentation for Connected Vehicle Dataset

## Summary
This document describes the UMTRI MAP dataset that is available on Flux through Globus Connect. The data represents the MAP messages used to provide intersection and roadway lane geometry data for one or more locations. Almost all roadway geometry information as well as roadway attributes (such as where a do not block region exists, or what maneuvers are legally allowed at a given point) is contained in the “generic lane” details of this message.  MAP messages are used in intersections to number and describe lane level details of each lane, while the SPAT message provides the current state of each signal head controlling the ability to stop/pass a given lane. 

## Data Filtering
No filtering has been done to MAP messages. 

## File Content Description
Each file is comma delimited. Files do have column headers.

## Data Size
The total size of the dataset is 8 KB.

## MapMD
Column Number|Name|Description|Units
---|---|---|---
1|RxDevice|Device Id of the RSE|none  
2|FileId|unique number assigned to each file; not the same FileId in the BSM dataset|none
3|TxDevice|Another RSE Device Id|none
4|Gentime|number of microseconds since Jan 1, 2004 (UTC +00:00)|microseconds  
5|MsgCount|MAP message count (restarts with new pcap file)|none
6|FrameOffset|
7|FrameSize|
8|MapRelOffset|
9|MapPayLoad|
10|GenTimeRelOffset|
11|Version|
12|MessageAttr|
13|Latitude|y-center of the intersection|degrees
14|Longitude|x-center of the intersection|degrees
15|Elevation|z-center of the intersection|decimeters
16|AEBCount|number of approach lanes, egress lanes, barriers|none

## AEB
Column Number|Name|Description|Units
---|---|---|---
1|RxDevice|Device Id of the RSE|none  
2|FileId|unique number assigned to each file; not the same FileId in the BSM dataset|none
3|TxDevice|Another RSE Device Id|none
4|MsgCount|MAP message count (restarts with new pcap file)|none
5|AEBCount|number of approach lanes, egress lanes, barriers|none
6|AEBType|1-approach, 2-egress, 3-barrier|none
7|LaneCount|Number of lanes in intersection|lanes
8|PriPreLoad|

## Lane
1|RxDevice|Device Id of the RSE|none  
2|FileId|unique number assigned to each file; not the same FileId in the BSM dataset|none
3|TxDevice|Another RSE Device Id|none
4|MsgCount|MAP message count (restarts with new pcap file)|none
5|AEB|
6|Lane|Lane Number
7|LaneType|
8|LaneId|
9|LaneAttr|
10|BarrierAttr|
11|Width|
12|ConnLaneId|
13|ConnCode|
14|RefLaneId|
15|RefLatOffset|
16|NodeLoad|
17|NodeAttr|
18|NodeNumOfPts|

## Node
Column Number|Name|Description|Units
---|---|---|---
1|RxDevice|Device Id of the RSE|none  
2|FileId|unique number assigned to each file; not the same FileId in the BSM dataset|none
3|TxDevice|Another RSE Device Id|none
4|MsgCount|MAP message count (restarts with new pcap file)|none
5|AEB|
6|Lane|Lane id
7|Node|Node id
8|NodeEastOff|
9|NodeNorthOff|
10|NodeEleOff|
11|NodeWidth|


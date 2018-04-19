# Signal, Phase and Timing Documentation for Connected Vehicle Dataset

## Summary
This document describes the UMTRI Signal, Phase and Timing (SPaT) filtered dataset that is available on Flux through Globus Connect.
The data represents the SPaT messages that are transmitted by Roadside Equipment (RSE) devices in the Plymouth corridor.

RxDevice|Location
---|---
18010|Plymouth and Barton
18013|Plymouth and Nixon
18014|Plymouth and Huron Parkway
18015|Plymouth and Green
18016|Plymouth and Murfin

Category|Value
---|---
RxDevices|5
Date Range|2015-03-14 to 2016-12-31 (Note: There is no data available earlier in 2015)

## Data Filtering
No filtering has bee done to the dataset with the exception of choice of RSE devices.

**Note**: For space considerations, not all available SPaT messages were uploaded to the Safety Pilot Database.

## Data Size
The total size of the dataset is about 1.0 TB (uncompressed).

## Variables
The **first five columns** represent the composite primary keys for the dataset.  

Column Number|Name|Description|Units
:---:|---|---|---
1|RxDevice|SPaT Id|none  
2|FileId|unique number assigned to each pcap file|none  
3|TxDevice|Another SPaT Id|none
4|MsgCount|SPaT message count|none
5|LaneId||none
6|Movement||none
7|State||none
8|MinTR||seconds  
9|MaxTR||seconds
10|YellowState|
11|YellowTime|
12|PedDect|
13|PedVehCount|

**Note**: I do not know the reason for two SPaT Ids. 
You would assume that they are always the same pairs in the dataset but you would be wrong.

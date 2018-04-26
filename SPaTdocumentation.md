# Signal, Phase and Timing Documentation for Connected Vehicle Dataset

## Table of Contents
- [Summary](#summary)
- [Data Filtering](#data-filtering)
- [File Content Description](#file-content-description)
- [Folder/File Naming Convention](#folder-and-file-naming-convention)
- [Data Size](#data-size)
- [Variables](#variables)
- [Reference](#reference)

## Summary
This document describes the UMTRI Signal, Phase and Timing (SPaT) dataset that is available on Flux through Globus Connect for 2015-2016. The data represents the SPaT messages that are transmitted by Roadside Equipment (RSE) devices in the Plymouth Road corridor.

RxDevice|Location|MAP Data Available
---|---|---
18010|Plymouth and Barton|No except MapMD
18012|Plymouth and Traverwood|Yes
18013|Plymouth and Nixon|Yes
18014|Plymouth and Huron Parkway|Yes
18015|Plymouth and Green|Yes
18022|Plymouth and Murfin|No except MapMD

Category|Value
---|---
RxDevices|6
Date Range|2015-03-14 to 2016-12-31 (Note: There is no data available earlier in 2015)

## Data Filtering
No filtering has been done to the SPaT messages. 

**Note**: Due to the amount of data, not all available SPaT messages were uploaded to the Safety Pilot Database.

## File Content Description
Each file is comma delimited.
Files do not have any column headers.

## Folder and File Naming Convention
Files are organized based on the day and RxDevice. The top level folder(s) is named `TripStart/spat`. The Year-Month sub-folders are labeled `YYYYMM`. The files are labeled `TripStart_4####_180##.csv` where 4#### represents the number of days since Dec. 30, 1899, and 180## represents the RxDevice. For example, TripStart_42077_18012.csv represents March 15, 2015 for the RSE at Plymouth and Traverwood.

## Data Size
The total size of the dataset is about 1.2 TB (uncompressed).

## Variables
The **first five columns** represent the composite primary keys for the dataset.  

Column Number|Name|Description|Units
:---:|---|---|---
1|RxDevice||Device Id of the RSE|none  
2|FileId|unique number assigned to each pcap file|none  
3|TxDevice|Another RSE Device Id|none
4|MsgCount|SPaT message count (restarts with new pcap file)|none
5|LaneId|lane number|none
6|Movement|indicates the beginning of a movement description|none
7|State|current state of a particular known movement|none
8|MinTR|minimum guaranteed amount of time remaining before the signal phase will change to the next phase|tenths of a second
9|MaxTR|anticipated maximum time remaining before the signal phase is predicted to change to the next phase|tenths of a second
10|YellowState|For motorized vehicle lanes, this object indicates next (yellow) signal state of all possible lights pertaining to a particular known movement after the current signal state expires. For pedestrian lanes, this data object indicates next active state of the crosswalk indicators for a particular known pedestrian movement.|none
11|YellowTime|duration of yellow signal phase|none
12|PedDect|possible presence of one or more pedestrians or other objects in the movements walk area|pedestrians
13|PedVehCount|estimated count of vehicles or pedestrians within a predefined time period|vehicles or pedestrians
14|Gentime|number of microseconds since Jan 1, 2004 (UTC +00:00)|microseconds

**Note**: I do not know the reason for two device ids. 
You would assume that the pairs of IDs do not have any other combinations in the dataset but you would be wrong.

## Reference
Variable definitions were taken from the Word document `J2735_SPATblob_MAPblob_RevC_20120217.docx` in the `TripStart/spat/documentation` folder.

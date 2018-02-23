# <font color='blue'>Received (Rx) Basic Safety Message Documentation for Connected Vehicle Dataset</font>

## Summary
This document describes the UMTRI Received Basic Safety Message (BSM) filtered dataset that is available on Flux through Globus Connect.
The data represents the BSMs that are **received** by vehicles that have Rx capability in the dataset.

Category|Value
---|---
Rx Vehicles|136
Number of V2V interactions|462,161
Number of Rx BSMs|68,574,994
Date Range|2012-09-20 to 2015-03-29

## Data Filtering
The dataset has been filtered according to the following guidelines:  
1. BSMs that can be found in the transmitted BSM filtered dataset

## File Content Description
Each file is comma delimited.  
Files **do not** have any column headers.  
Each file contains all the Rx BSMs on a given day (i.e. TripStart).  

## Folder/File Naming Convention
Files are organized into folders based on the month the trip occurred. The top level folder(s) is named `TripStart\bsmRx`. The Year-Month sub-folders are labeled `YYYYMM`. The files are labeled `TripStart_bsmrx_4####.csv` where `4####` represents the number of days since Dec. 30, 1899.  For example, `TripStart_bsmrx_41172.csv` represents Sep. 20, 2012. 

## Data Size
The total size of the dataset is about 9 GB (uncompressed).

## Variables
The **first four columns** represent the composite primary keys for the dataset.  

Column Number|Rx/Tx Vehicle|Name|Description|Units
:---:|:---:|---|---|---
1|Rx|RxDevice|receiving Device Id; equivalent to VehicleID|none  
2|Rx|FileId|unique number assigned to each pcap file|none  
3|Tx|TxDevice|sending Device Id (static 2 bytes of the BSM 4 byte temporary Id)|none  
4|Tx|Gentime|number of microseconds since Jan 1, 2004 (UTC +00:00)|microseconds  
5|Tx|TxRandom|random id  (random 2 bytes of the BSM 4 byte temporary Id)|none  
6|Tx|MsgCount|BSM message count|none  
7|Tx|DSecond|number of milliseconds in the current minute|milliseconds  
8|Tx|Latitude|GPS latitude position|degrees  
9|Tx|Longitude|GPS longitude position|degrees  
10|Tx|Elevation|GPS elevation|meters  
11|Tx|Speed|GPS estimated speed|meters/second 
12|Tx|Heading|GPS heading; 0/90/180/270 corresponds respectively to north/east/south/west|degrees  
13|Tx|Ax|estimated longitudinal acceleration|meters/second^2  
14|Tx|Ay|estimated lateral acceleration|meters/second^2  
15|Tx|Az|estimated vertical acceleration|meters/second^2  
16|Tx|Yawrate|estimated yaw rate; negative/positive values corresponds respectively to left/right turns|degrees/second
17|Tx|PathCount|number of points in the path history|none
18|Tx|RadiusOfCurve|estimated path prediction value|1/meter  
19|Tx|Confidence|confidence in the path prediction|%  

## Primary Keys
Data|Primary Key(s)|Note
---|---|---
Vehicle|`RxDevice` or `TxDevice`|
V2V Interaction|`RxDevice`, `FileId`, `TxDevice`|
BSM|`RxDevice`, `FiledId`, `TxDevice`, `Gentime`|

## Metadata
**umtri_bsmrx_metadata.csv** is a file containing some summary statistics for each V2V interaction. The metadata file does have column headers. 

Column Number|Rx/Tx Vehicle|Name|Description|Units
:---:|:---:|---|---|---
1||TripStart|number of days since Dec. 30, 1899|days  
2|Rx|RxDevice|receiving Device Id; equivalent to VehicleID|none  
3|Rx|FileId_rx<sup>*</sup>|unique pcap file number on RxDevice for rx variables|none
4|Rx|FileId_tx|unique pcap file number on RxDevice for tx variables|none  
5|Tx|TxDevice|sending Device Id (static 2 bytes of the BSM 4 byte temporary Id)|none  
6|Rx|firstHeading_rx<sup>*</sup>|GPS heading of first BSM during V2V; 0/90/180/270 corresponds respectively to north/east/south/west|degrees
7|Tx|firstHeading_tx|GPS heading of first BSM during V2V; 0/90/180/270 corresponds respectively to north/east/south/west|degrees
8|Rx|firstLatitude_rx<sup>*</sup>|GPS latitude of first BSM during V2V|degrees  
9|Tx|firstLatitude_tx|GPS latitude of first BSM during V2V|degrees  
10|Rx|firstLongitude_rx<sup>*</sup>|GPS longitude of first BSM during V2V|degrees  
11|Tx|firstLongitude_tx|GPS longitude of first BSM during V2V|degrees  
12|Rx|firstSpeed_rx<sup>*</sup>|GPS estimated speed of first BSM during V2V|mph 
13|Tx|firstSpeed_tx|GPS estimated speed of first BSM during V2V|mph
14|Rx|lastHeading_rx<sup>*</sup>|GPS heading of last BSM during V2V; 0/90/180/270 corresponds respectively to north/east/south/west|degrees
15|Tx|lastHeading_tx|GPS heading of last BSM during V2V; 0/90/180/270 corresponds respectively to north/east/south/west|degrees
16|Rx|lastLatitude_rx<sup>*</sup>|GPS latitude reading of last BSM during V2V|degrees  
17|Tx|lastLatitude_tx|GPS latitude reading of last BSM during V2V|degrees  
18|Rx|lastLongitude_rx<sup>*</sup>|GPS longitude reading of last BSM during V2V|degrees  
19|Tx|lastLongitude_tx|GPS longitude reading of last BSM during V2V|degrees  
20|Rx|lastSpeed_rx<sup>*</sup>|GPS estimated speed of last BSM during V2V|mph 
21|Tx|lastSpeed_tx|GPS estimated speed of last BSM during V2V|mph
22|Rx|maxSpeed_rx<sup>*</sup>|maximum GPS estimated speed during V2V|mph
23|Tx|maxSpeed_tx|maximum GPS estimated speed during V2V|mph
24|Rx|avgSpeed_rx<sup>*</sup>|mean GPS estimated speed during V2V|mph
25|Tx|avgSpeed_tx|mean GPS estimated speed during V2V|mph
26|Rx|minLon_rx<sup>*</sup>|minimum GPS longitude during V2V|degrees
27|Rx|minLat_rx<sup>*</sup>|minimum GPS latitude during V2V|degrees
28|Rx|maxLon_rx<sup>*</sup>|maximum GPS longitude during V2V|degrees
29|Rx|maxLat_rx<sup>*</sup>|maximum GPS latitude during V2V|degrees
30|Tx|minLon_tx|minimum GPS longitude during V2V|degrees
31|Tx|minLat_tx|minimum GPS latitude during V2V|degrees
32|Tx|maxLon_tx|maximum GPS longitude during V2V|degrees
33|Tx|maxLat_tx|maximum GPS latitude during V2V|degrees
34|Tx|firstTime|timestamp of first BSM during V2V|datetime
35|Tx|lastTime|timestamp of last BSM during V2V|datetime
36|Rx|duration_rx|time duration of V2V; omits time jumps greater than 1 second from calculation|seconds
37|Tx|duration_tx|time duration of V2V; omits time jumps greater than 1 second from calculation|seconds
38|Rx|distance_rx|travelled distance during V2V; based on vehicle speed; omits time jumps greater than 1 second from calculation|feet
39|Tx|distance_tx|travelled distance during V2V; based on vehicle speed; omits time jumps greater than 1 second from calculation|feet
40|Tx|bsmCount|number of received basic safety messages (equivalent to rows) during V2V|none
41|Rx|deltaTmax_rx|maximum time between consecutive timestamps; can be thought of as a measure of data quality; ideally it would be 0.100 seconds|none
42|Tx|deltaTmax_tx|maximum time between consecutive timestamps; can be thought of as a measure of data quality; ideally it would be 0.100 seconds|none
43||firstDistBtwVeh<sup>*</sup>|great-circle distance between the two vehicles of first BSMs|feet
44||lastDistBtwVeh<sup>*</sup>|great-circle distance between the two vehicles of last BSMs|feet

<sup>*</sup>These fields can have null values. If null, it indicates that no bsm was found for that RxDevice between the firstTime-0.1s and lastTime+0.1s. Other dependent fields like duration, distance and deltaTmax have been set to 0 in this case.

## Coordinate Reference System
GPS coordinates are in WGS84 or EPSG:4326

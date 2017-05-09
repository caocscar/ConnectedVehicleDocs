# <font color='blue'>Received (Rx) Basic Safety Message Documentation for Connected Vehicle Dataset</font>

## Summary
This document describes the UMTRI Received Basic Safety Message (BSM) filtered dataset that is available on Flux through Globus Connect.
The data represents the BSMs that are **received** by vehicles that have Rx capability in the dataset.

Category|Value
---|---
Rx Vehicles|136
Rx BSMs|462161
Date Range|2012-09-20 to 2015-03-29

## Data Filtering
The dataset has been filtered according to the following guidelines:  
1. BSMs that can be found in the transmitted BSM filtered dataset

## File Content Description
Each file is comma delimited.  
Files **do not** have any column headers.  
Each file contains all the Rx BSMs on a given day (i.e. TripStart).  

## Folder/File Naming Convention
Files are organized into folders based on the month and day the trip started. The top level folder(s) is named `TripStart\bsmRx`. The Year-Month sub-folders are labeled `YYYYMM`. 
The files are labeled `TripStart_bsmrx_4####.csv` where `4####` represents the number of days since Dec. 30, 1899.  For example, `TripStart_bsmrx_41172.csv` represents Sep. 20, 2012. 

## Data Size
The total size of the dataset is about 10 GB (uncompressed).

## Variables
The **first four columns** represent the composite primary keys for the dataset.  

Column Number|Rx/Tx Vehicle|Name|Description|Units
:---:|:---:|---|---|---
1|Rx|RxDevice|receiving Device Id; equivalent to VehicleID|none  
2|Rx|FileId|unique number assigned to each pcap file|none  
3|Tx|TxDevice|sending Device Id (static 2 bytes of the BSM 4 byte temporary Id)|none  
4|Tx|Gentime|number of microseconds since Jan 1, 2004|microseconds  
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
**umtri_bsmrx_metadata.csv** is a file containing some summary statistics for each V2V interaction. Each row represents one received BSM. The metadata file does have column headers. 

Column Number|Rx/Tx Vehicle|Name|Description|Units
:---:|:---:|---|---|---
1||TripStart|number of days since Dec. 30, 1899|days  
2|Rx|RxDevice|receiving Device Id; equivalent to VehicleID|none  
3|Rx|FileId_rx|unique pcap file number on RxDevice for rx variables|none
4|Rx|FileId_tx|unique pcap file number on RxDevice for tx variables|none  
5|Tx|TxDevice|sending Device Id (static 2 bytes of the BSM 4 byte temporary Id)|none  
6|Rx|firstHeading_rx|GPS heading of first BSM during V2V; 0/90/180/270 corresponds respectively to north/east/south/west|degrees
7|Tx|firstHeading_tx|GPS heading of first BSM during V2V; 0/90/180/270 corresponds respectively to north/east/south/west|degrees
8|Rx|firstLatitude_rx|GPS latitude of first BSM during V2V|degrees  
9|Tx|firstLatitude_tx|GPS latitude of first BSM during V2V|degrees  
10|Rx|firstLongitude_rx|GPS longitude of first BSM during V2V|degrees  
11|Tx|firstLongitude_tx|GPS longitude of first BSM during V2V|degrees  
12|Rx|firstSpeed_rx|GPS estimated speed of first BSM during V2V|meters/second 
13|Tx|firstSpeed_tx|GPS estimated speed of first BSM during V2V|meters/second
14|Rx|lastHeading_rx|GPS heading of last BSM during V2V; 0/90/180/270 corresponds respectively to north/east/south/west|degrees
15|Tx|lastHeading_tx|GPS heading of last BSM during V2V; 0/90/180/270 corresponds respectively to north/east/south/west|degrees
16|Rx|lastLatitude_rx|GPS latitude reading of last BSM during V2V|degrees  
17|Tx|lastLatitude_tx|GPS latitude reading of last BSM during V2V|degrees  
18|Rx|lastLongitude_rx|GPS longitude reading of last BSM during V2V|degrees  
19|Tx|lastLongitude_tx|GPS longitude reading of last BSM during V2V|degrees  
20|Rx|lastSpeed_rx|GPS estimated speed of last BSM during V2V|meters/second 
21|Tx|lastSpeed_tx|GPS estimated speed of last BSM during V2V|meters/second
5|Tx|TxRandom|random id  (random 2 bytes of the BSM 4 byte temporary Id)|none  
6|Tx|MsgCount|BSM message count|none  
7|Tx|DSecond|number of milliseconds in the current minute|milliseconds  
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

*Note:* These field can be blank. If blank field, it indicates that no bsm was found for that RxDevice between the firstTime and lastTime

## Coordinate Reference System
GPS coordinates are in WGS84 or EPSG:4326

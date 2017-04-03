# <font color='blue'>Received (Rx) Basic Safety Message Documentation for Connected Vehicle Dataset</font>

## Summary
This document describes the UMTRI Received Basic Safety Message (BSM) filtered dataset that is available on Flux through Globus Connect.
The data represents the BSMs that are **received** by vehicles that have Rx capability in the dataset.

Category|Value
---|---
Rx Vehicles|136
Rx BSMs|Forthcoming
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

## Coordinate Reference System
GPS coordinates are in WGS84 or EPSG:4326

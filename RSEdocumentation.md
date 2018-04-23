# Roadside Equipment Documentation for Connected Vehicle Dataset

## Table of Contents
- [Summary](#summary)
- [Roadside Equipment](#roadside-equipment)
- [Data Filtering](#data-filtering)
- [File Content Description](#file-content-description)
- [Folder/File Naming Convention](#folder-and-file-naming-convention)
- [Data Size](#data-size)
- [Variables](#variables)
- [Metadata](#metadata)
- [Coordinate Reference System](#coordinate-reference-system)

## Summary
This document describes the UMTRI Roadside Equipment (RSE) dataset that is available on Flux through Globus Connect. The dataset contains **received** BSMs from vehicles.

Category|Value
---|---
Number of RSE units|29
Number of V2I interactions|6,375,343
Number of BSMs|3.5 billion
Date Range|2012-08-08 to 2016-10-03

## Roadside Equipment
_RseDevice.csv_ contains the location and description of each RSE.

## Data Filtering
The dataset has been filtered according to the following guidelines:
- Only Vehicle-To-Infrastructure communication (V2I) involving a vehicle driving that day and during that time was included (as determined from the Basic Safety Message (BSM) dataset).  
**Note**: Due to rounding of datetimes in the metadata, there will be some V2I BSM messages that fall outside the BSM dataset by a second or less.

## File Content Description
Each file is comma delimited.  
Files **do not** have any column headers.  
Each file contains all V2I for that TripStart day.

## Folder and File Naming Convention
Files are organized into folders based on the month and day the V2I occurred. The top level folder(s) is named `TripStart\rse`. The Year-Month sub-folders are labeled `YYYYMM`. The Day files are labeled `TripStart_4####` where `4####` represents the number of days since Dec. 30, 1899. For example, TripStart_41092 represents July 2, 2012. 

## Data Size
The total size of the dataset is about 444 GB (uncompressed).

## Variables
The **first four columns** represent the primary keys for the dataset.  
The Tx columns should be identical to the same message in the BSM dataset.

Column Number|Rx/Tx Device|Name|Description|Units
:---:|:---:|---|---|---
1|Rx|RxDevice|Device Id of the RSE|none  
2|Rx|FileId|unique number assigned to each file; not the same FileId in the BSM dataset|none
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

# Metadata
*umtri_rse_metadata.csv* is a file containing some summary statistics for each V2I interaction.
The metadata file does have column headers.

Column Number|Name|Description|Units
:---:|---|---|---
1|TripStart|number of days since Dec. 30, 1899; day where the V2I messages can be found|days
2|RxDevice|receiving Device Id of the RSE|none
3|FileId|unique number assigned to each file; not the same FileId in the BSM dataset|none
4|TxDevice|sending Device Id (static 2 bytes of the BSM 4 byte temporary Id)|none
5|firstLatitude|GPS Latitude Position of first BSM during V2I|degrees
6|firstLongitude|GPS Longitude Position of first BSM during V2I|degrees
7|lastLatitude|GPS Latitude Position of last BSM during V2I|degrees
8|lastLongitude|GPS Longitude Position of last BSM during V2I|degrees
9|firstSpeed|GPS estimated speed of first BSM during V2I|mph
10|lastSpeed|GPS estimated speed of last BSM during V2I|mph
11|maxSpeed|maximum GPS estimated speed during V2I|mph
12|avgSpeed|mean GPS estimated speed during V2I|mph
13|firstTime|timestamp of first BSM during V2I|datetime
14|lastTime|timestamp of last BSM during V2I|datetime
15|duration|time duration of V2I; omits time jumps greater than 1 second from calculation|seconds
16|distance|travelled distance during V2I; based on vehicle speed; omits time jumps greater than 1 second from calculation|feet
17|bsmCount|number of basic safety messages (equivalent to rows) during V2I|none
18|deltaTmax|maximum time between consecutive timestamps; can be thought of as a measure of data quality; ideally it would be 0.100 seconds|seconds

## Coordinate Reference System
GPS coordinates are in WGS84 or EPSG:4326


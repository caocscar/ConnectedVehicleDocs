# <font color='blue'>Basic Safety Message Documentation for Connected Vehicle Dataset</font>

## Summary
This document describes the UMTRI Basic Safety Message (BSM) filtered dataset that is available on Flux through Globus Connect. The data represents the BSMs that are **transmitted** by each vehicle in the dataset.

## Data Filtering
The dataset has been filtered according to the following guidelines:  
1. A random portion (between 3-8%) of each trip has been removed from the beginning and end of each trip.  
2. Trips that are less than 2 minutes OR 1 kilometer have been removed.

## File Content Description
Each file contains data from 55 or fewer trips. Trips (and thus files) within a directory are pseudo-sorted by `RxDevice` then by `FileId`.

## Naming Convention
Files are organized into directories based on the month and day the trip started. The top level folder(s) is named `TripStart\bsm`. The Year-Month sub-directories are labeled `YYYYMM`. The Day sub-directories are labeled `TripStart_4####` where `4####` represents the number of days since Dec. 30, 1899. For example, TripStart_41092 represents July 2, 2012. Within each directory, are csv files labeled `TripStart_4####_p???` where `4####` represents the same as above and `???` represents the part file number for that day. 

## Data Size
The total size of the dataset is about 5.4 TB (uncompressed).

## Variables
Files **do not** have any column headers. Below is a list of the variable description containing:  
i) column number  
ii) column name (based on SQL Server table)  
iii) column description  
iv) units  

The **first four columns** represent the composite primary keys for the dataset.  
1.  RxDevice - receiving Device Id (For VADs this is the same as TxDevice); equivalent to VehicleID [no units]  
2.  FileId - unique number assigned to each pcap file; [no units]  
3.  TxDevice - sending Device Id (static 2 bytes of the BSM 4 byte temporary Id) [no units]  
4.  Gentime - number of microseconds since Jan 1, 2004 [microseconds]  
5.  TxRandom - random id  (random 2 bytes of the BSM 4 byte temporary Id) [no units]  
6.  MsgCount - BSM message count [no units]  
7.  DSecond - number of milliseconds in the current minute [milliseconds]  
8.  Latitude - GPS latitude position [degrees]  
9.  Longitude - GPS longitude position [degrees]  
10. Elevation - GPS elevation [meters]  
11. Speed - GPS estimated speed [m/s]  
12. Heading - GPS heading; 0/90/180/270 corresponds respectively to north/east/south/west [degrees]  
13. Ax - estimated longitudinal acceleration [m/s^2]  
14. Ay - estimated lateral acceleration [m/s^2]  
15. Az - estimated vertical acceleration [m/s^2]  
16. Yawrate - estimated yaw rate; negative/positive values corresponds respectively to left/right turns [deg/s]  
17. PathCount - number of points in the path history [no units]  
18. RadiusOfCurve - estimated path prediction value [1/m]  
19. Confidence - confidence in the path prediction [%]  

## Primary Keys
These are the primary key(s) for the following items:
- Vehicle - `RxDevice` column
- Trip - `RxDevice`, `FileId`, `TxDevice` columns (**Note**: when `RxDevice` == `TxDevice`, the `RxDevice` and `FileId` columns will suffice)
- BSM - `RxDevice`, `FiledId`, `TxDevice`, `Gentime` columns

## Metadata
_umtri_bsm_metadata.csv_ is a file containing some summary statistics for each trip. Each row represents one trip.
The metadata file does have column headers. Below is a list of the variable description containing:  
i) column number  
ii) column name  
iii) column description  
iv) units

**RxDevice, fileId, TxDevice** represent the composite primary keys for the metadata.  
1.  TripStart - number of days since Dec. 30, 1899; folder where the trip can be found  [no units]  
2.  fileNum - file number where the trip can be found [no units]  
3.  RxDevice - receiving Device Id (For VADs this is the same as TxDevice) [no units]  
4.  fileId - unique number assigned to each pcap file [no units]  
5.  TxDevice - sending Device Id (static 2 bytes of the BSM 4 byte temporary Id) [no units]  
6.  firstLatitude - GPS Latitude Position of first BSM in the trip [degrees]  
7.  firstLongitude - GPS Longitude Position of first BSM in the trip [degrees]  
8.  lastLatitude - GPS Latitude Position of last BSM in the trip [degrees]  
9.  lastLongitude - GPS Longitude Position of last BSM in the trip [degrees]  
10. firstSpeed - GPS estimated speed of first BSM in the trip [mph]  
11. lastSpeed - GPS estimated speed of last BSM in the trip [mph]  
12. maxSpeed - maximum GPS estimated speed during trip [mph]  
13. avgSpeed - mean GPS estimated speed during trip [mph]  
14. avgSpeed_pts_gte_1mph - mean GPS estimated speed during trip while vehicle was moving faster than 1mph [mph]  
15. firstTime - timestamp of first BSM in the trip [datetime]  
16. lastTime - timestamp of last BSM in the trip [datetime]  
17. duration - time duration of the trip; omits time jumps greater than 1 second from calculation [min]  
18. distance - travelled distance of the trip; based on vehicle speed; omits time jumps greater than 1 second from calculation [km]  
19. bsmCount - number of basic safety messages (equivalent to rows) in the trip [no units]  
20. deltaTmax - maximum time between consecutive timestamps; can be thought of as a measure of data quality; ideally it would be 0.100 seconds [s]  

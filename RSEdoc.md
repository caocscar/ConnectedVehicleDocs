# <font color='blue'>Roadside Equipment Documentation for Connected Vehicle Dataset</font>

## Summary
This document describes the UMTRI Roadside Equipment (RSE) dataset that is available on Flux through Globus Connect. The dataset contains **received** BSMs from vehicles.

## Roadside Equipment
_RseDevice.csv_ contains the location and description of each RSE.

## Data Filtering
The dataset has been filtered according to the following guidelines:
- Only Vehicle-To-Infrastructure communication (V2I) involving a vehicle driving that day and during that time was included (as determined from the Basic Safety Message (BSM) dataset).  
**Note**: Due to rounding of datetimes in the metadata, there will be some V2I BSM messages that fall outside the BSM dataset by a second or less.

## File Content Description
Each file contains all V2I for that TripStart day.

## Folder/File Naming Convention
Files are organized into folders based on the month and day the V2I occurred. The top level folder(s) is named `TripStart\rse`. The Year-Month sub-folders are labeled `YYYYMM`. The Day files are labeled `TripStart_4####` where `4####` represents the number of days since Dec. 30, 1899. For example, TripStart_41092 represents July 2, 2012. 

## Data Size
The total size of the dataset is about 444 GB (uncompressed).

## Variables
Files **do not** have any column headers. Below is a list of the variable description containing:  
i) column number  
ii) column name (based on SQL Server table)  
iii) column description  
iv) units

The **first four columns** represent the primary keys for the dataset.  
1.  RxDevice - receiving Device Id of the RSE [no units]  
2.  FileId - unique number assigned to each file; not the same FileId in the BSM dataset [no units]

The rest of the columns should be identical to the same message in the BSM dataset  
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

# Metadata
*umtri_rse_metadata.csv* is a file containing some summary statistics for each V2I interaction.
The metadata file does have column headers. Below is a list of the variable description containing:  
i) column number  
ii) column name  
iii) column description  
iv) units

1.  TripStart - number of days since Dec. 30, 1899; day where the V2I messages can be found [days]
2.  RxDevice - receiving Device Id of the RSE [no units]
3.  FileId - unique number assigned to each file; not the same FileId in the BSM dataset [no units]
4.  TxDevice - sending Device Id (static 2 bytes of the BSM 4 byte temporary Id) [no units]
5.  firstLatitude - GPS Latitude Position of first BSM during V2I [degrees]
6.	firstLongitude - GPS Longitude Position of first BSM during V2I [degrees]
7.  lastLatitude - GPS Latitude Position of last BSM during V2I [degrees]
8.	lastLongitude - GPS Longitude Position of last BSM during V2I [degrees]
9.	firstSpeed - GPS estimated speed of first BSM during V2I [mph]
10. lastSpeed - GPS estimated speed of last BSM during V2I [mph]
11. maxSpeed - maximum GPS estimated speed during V2I [mph]
12. avgSpeed - mean GPS estimated speed during V2I [mph]
13. firstTime - timestamp of first BSM during V2I [datetime]
14. lastTime - timestamp of last BSM during V2I [datetime]
15. duration - time duration of V2I; omits time jumps greater than 1 second from calculation [s]
16. distance - travelled distance during V2I; based on vehicle speed; omits time jumps greater than 1 second from calculation [m]
17.	bsmCount - number of basic safety messages (equivalent to rows) during V2I [no units]
18.	deltaTmax - maximum time between consecutive timestamps; can be thought of as a measure of data quality; ideally it would be 0.100 seconds [s]

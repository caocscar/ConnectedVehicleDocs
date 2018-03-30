# Stop Sign Intersection Data Nugget Documentation

## Intersection Queries for Safety Pilot Data

The goal of this query was to pull data to analyze the behavior of drivers approaching stop sign-controlled intersections.
The following intersections were picked from the Safety Pilot study area:

4 Way / 4 Stop|4 Way / 2 Stop|3 Way / 1 Stop|3 Way / 3 Stop
---|---|---|---
Murfin and Hubbard|Plymouth and N Earhart/Old Earhart|Green and Baxter|Hayward and Beal
Scio Church and Wagner|Earhart and Ava Marie/Whitehall|Green and Hubbard|Tappan and Monroe
Hill and East U|Hill and Oakland|Plymouth and Prairie|South U and East U
Church and Willard|Pontiac Trail and Dhu Varren|Willard and East U|State and South U
Green and Glazier Way|W Summit and Wildt/Hiscock|Washington and Fletcher|Liberty and Maynard

These intersections were queried for all activity within one year’s time of the study.  

For the 3 Way / 3 Stop and 4 Way / 4 Stop intersections, all vehicles approaching the intersection were of interest.
To select these vehicles, the lat/lng coordinates of each intersection were identified and used to generate a 
bounding box 300 feet in each cardinal direction from the center of the intersection. 

Here is an example of one of these queries:

``` sql
SELECT * 
FROM BsmP1 
WHERE Gentime > 284083200000000 AND Gentime < 315619200000000 
AND Latitude > 42.2871868 AND Latitude < 42.2888332 
AND Longitude > -83.693449 AND Longitude < -83.691231
```

For the 4 Way / 2 Stop queries, the query was split to handle both incoming stop-controlled approaches and headings.
Instead of using a region centered on the intersection, the regions were chosen extending from the center of the intersection,
300 feet in the cardinal direction of the incoming stop-controlled road. In the case of roads with headings in non-cardinal directions, this region was chosen as the quadrant of the incoming road.  All traffic within the target zone within 22.5 degrees of the heading of the approaching road were included in the query.  3 Way / 1 Stop queries worked similarly, but with only one pair of region and heading used as criteria.
These queries were as follows:

4 Way / 2 Stop:

``` sql
SELECT * 
FROM BsmP1 
WHERE Gentime > 284083200000000 AND Gentime < 315619200000000 
AND ( 
  Latitude > 42.30773 AND Latitude < 42.3085532
  AND Longitude > -83.6832872 AND Longitude < -83.6827328
  AND Heading > 157.5 AND Heading < 202.5
) OR (
  Latitude > 42.3069068 AND Latitude < 42.30773
  AND Longitude > -83.6832872 AND Longitude < -83.6827328
  AND Heading > 337.5 OR Heading < 22.5
)
```

3 Way 1 Stop:

``` sql
SELECT * 
FROM BsmP1 
WHERE Gentime > 284083200000000 AND Gentime < 315619200000000 
AND  Latitude > 42.30266 AND Latitude < 42.3034832 
AND Longitude > -83.7024272 AND Longitude < -83.7018728 
AND Heading > 157.5 AND Heading < 202.5
```

## File Headers
The column headers are the same as for the transmitted BSM dataset. [See here.](https://github.com/caocscar/ConnectedVehicleDocs/blob/master/BSMdocumentation.md#variables)



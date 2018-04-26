# Summary of Documentation Files
## Main Datasets
[Documentation for transmitted Basic Safety Message (BSM)](BSMdocumentation.md)  
[Documentation for received (Rx) Basic Safety Message (BSM)](BSMRxdocumentation.md)  
[Documentation for Roadside Equipment (RSE)](RSEdocumentation.md)  
[Documentation for Signal, Phase and Timing (SPaT) Messages](SPaTdocumentation.md)  
[Documentation for MAP Messages](MAPdocumentation.md)

A high-level look at the variables in some of these dataset is available [here](http://www-personal.umich.edu/~scunchen/Mcity/tree/).

## Data Nuggets
Data nuggets are usually smaller datasets that are either:
1. A subset of the main datasets (with the exception of video) that fulfill some criteria
2. A new dataset from another source

Here is a list of them:
- Close By Vehicle Pairs
- Lane Change
- Lane Following
- Left Turn Signalized Intersections
- Left Turn Time Series
- [Plymouth Intersection Documentation](PlymouthIntersection.md) 
- [Stop Sign Intersection Documentation](StopSignIntersection.md)
- Traffic Flow Incidents

The data nuggets without a link should have documentation within the folder itself.

## Example BSM Code
This github page has some example Python code for analysis in a Jupyter Notebook.  
https://github.com/mcity/BSMexamplecode

**Note:** The external files (dependencies) are not included as part of the repository. The examples are meant to be illustrative and not necessarily reproducible. That could change if there are requests to do so.

# Citation
If you would like to cite the dataset provided, here is one suggestion:  
> The dataset contained de-identified Basic Safety Messages (BSM) collected from vehicles equipped with Dedicated Short Range Communication (DSRC) during the Connected Vehicle Safety Pilot Model Deployment program (Bezzina, D., & Sayer, J., 2015).

A copy of the final report can be found at the [NHTSA website](https://www.nhtsa.gov/sites/nhtsa.dot.gov/files/812171-safetypilotmodeldeploydeltestcondrtmrep.pdf), and the suggested citation format is:
> Bezzina, D., & Sayer, J. (2015, June). Safety pilot model deployment: Test conductor team report. (Report No. DOT HS 812 171). Washington, DC: National Highway Traffic Safety Administration.)

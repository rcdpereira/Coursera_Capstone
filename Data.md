# Data Evaluation

The dataset for the UK road accidents was obtained from the following source: [UK Road Safety Accidents and Vehicles](https://www.kaggle.com/tsiaras/uk-road-safety-accidents-and-vehicles).
There are two available datasets: Accident_Information and Vehicle_Information. A full metadata was not available.

The source describes both data:
* Accident_Information.csv: every line in the file represents a unique traffic accident (identified by the AccidentIndex column), featuring various properties related to the accident as columns. Date range: 2005-2017.
* Vehicle_Information.csv: every line in the file represents the involvement of a unique vehicle in a unique traffic accident, featuring various vehicle and passenger properties as columns. Date range: 2004-2016.
The datasets can be merged together through the accident identifier (Accident_Index).

## First Data Evaluation - Cleaning
### Removing non-relevant features
A thorough evaluation shall be conducted in order to define which features seem to influence the accidents severity. At first, let's take a look at the available features from each dataset.
From the *Accident_Information.csv* the following features exist: 

 0. Accident_Index  
 1. 1st_Road_Class  
 2. 1st_Road_Number  
 3. 2nd_Road_Class  
 4. 2nd_Road_Number  
 5. Accident_Severity  
 6. Carriageway_Hazards  
 7. Date  
 8. Day_of_Week  
 9. Did_Police_Officer_Attend_Scene_of_Accident  
10. Junction_Control
11. Junction_Detail  
12. Latitude  
13. Light_Conditions  
14. Local_Authority_(District)  
15. Local_Authority_(Highway)  
16. Location_Easting_OSGR  
17. Location_Northing_OSGR  
18. Longitude  
19. LSOA_of_Accident_Location  
20. Number_of_Casualties  
21. Number_of_Vehicles  
22. Pedestrian_Crossing-Human_Control  
23. Pedestrian_Crossing-Physical_Facilities  
24. Police_Force  
25. Road_Surface_Conditions  
26. Road_Type  
27. Special_Conditions_at_Site  
28. Speed_limit  
29. Time  
30. Urban_or_Rural_Area  
31. Weather_Conditions  
32. Year  
33. InScotland  

From the *Vehicle_Information.csv* the features are:

 0. Accident_Index  
 1. Age_Band_of_Driver  
 2. Age_of_Vehicle  
 3. Driver_Home_Area_Type  
 4. Driver_IMD_Decile  
 5. Engine_Capacity_.CC.  
 6. Hit_Object_in_Carriageway  
 7. Hit_Object_off_Carriageway  
 8. Journey_Purpose_of_Driver  
 9. Junction_Location  
10. make  
11. model  
12. Propulsion_Code  
13. Sex_of_Driver  
14. Skidding_and_Overturning  
15. Towing_and_Articulation  
16. Vehicle_Leaving_Carriageway  
17. Vehicle_Location.Restricted_Lane  
18. Vehicle_Manoeuvre  
19. Vehicle_Reference  
20. Vehicle_Type  
21. Was_Vehicle_Left_Hand_Drive  
22. X1st_Point_of_Impact  
23. Year  

From the features above, there are several columns that clearly won't have an impact on predicting severity of the accidents. These shall be droped from the assembled dataframes as a first step.

From Accident_Information.csv:

 1. 1st_Road_Class  
 2. 1st_Road_Number  
 3. 2nd_Road_Class  
 4. 2nd_Road_Number 
 9. Did_Police_Officer_Attend_Scene_of_Accident  
12. Latitude  
14. Local_Authority_(District)  
15. Local_Authority_(Highway)  
16. Location_Easting_OSGR  
17. Location_Northing_OSGR  
18. Longitude  
19. LSOA_of_Accident_Location  
33. InScotland  

From Vehicle_Information.csv:

10. make  
11. model  
12. Propulsion_Code  

Also, the Accidents dataset ranges from year 2005 to 2017, while the Vehicle dataset ranges from 2004 to 2016. Therefore, the rows in the Accidents data where `year == 2017` are be eliminated, while the Vehicles data are cleared of the rows with `year == 2004`.

### Removing "Data missing or out of range"
After the first step of cleaning data (removing the unwanted columns and years where no intersection exists between the two datasets), an evaluation on the available data is realised to check the frequency of null values (or, as stated in the datasets, Data missing or out of range). If a column contains significant amounts of null values, these have to be removed in order to not compromise the analysis.



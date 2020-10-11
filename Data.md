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

 |Table 1:                   |Accident_Information.csv features           |                                  |                                        |
 |:---                       |:---                                        |:---                              |:---                                    | 
 |Accident_Index             |1st_Road_Class                              |1st_Road_Number                   |2nd_Road_Class                          | 
 |2nd_Road_Number            |Accident_Severity                           |Carriageway_Hazards               |Date                                    |
 |Day_of_Week                |Did_Police_Officer_Attend_Scene_of_Accident |Junction_Control                  |Junction_Detail                         |
 |Latitude                   |Light_Conditions                            |Local_Authority_(District)        |Local_Authority_(Highway)               |
 |Location_Easting_OSGR      |Location_Northing_OSGR                      |Longitude                         |LSOA_of_Accident_Location               |
 |Number_of_Casualties       |Number_of_Vehicles                          |Pedestrian_Crossing-Human_Control |Pedestrian_Crossing-Physical_Facilities |
 |Police_Force               |Road_Surface_Conditions                     |Road_Type                         |Special_Conditions_at_Site              |
 |Speed_limit                |Time                                        |Urban_or_Rural_Area               |Weather_Conditions                      |
 |Year                       |InScotland                                  |  

From the *Vehicle_Information.csv* the features are:

|Table 2:                    |Vehicle_Information.csv features            |                                  |                                        |
|:---                        |:---                                        |:---                              |:---                                    |
|Accident_Index              |Age_Band_of_Driver                          |Age_of_Vehicle                    |Driver_Home_Area_Type                   |
|Driver_IMD_Decile           |Engine_Capacity_.CC.                        |Hit_Object_in_Carriageway         |Hit_Object_off_Carriageway              |
|Journey_Purpose_of_Driver   |Junction_Location                           |make                              |model                                   |
|Propulsion_Code             |Sex_of_Driver                               |Skidding_and_Overturning          |Towing_and_Articulation                 |
|Vehicle_Leaving_Carriageway |Vehicle_Location.Restricted_Lane            |Vehicle_Manoeuvre                 |Vehicle_Reference                       |
|Vehicle_Type                |Was_Vehicle_Left_Hand_Drive                 |X1st_Point_of_Impact              |Year                                    |

From the features above, there are several columns that clearly won't have an impact on predicting severity of the accidents. These shall be droped from the assembled dataframes as a first step.

From Accident_Information.csv:
**1st_Road_Class, 1st_Road_Number, 2nd_Road_Class, 2nd_Road_Number, Did_Police_Officer_Attend_Scene_of_Accident, Latitude, Local_Authority_(District), Local_Authority_(Highway), Location_Easting_OSGR, Location_Northing_OSGR, Longitude, LSOA_of_Accident_Location, InScotland.**  

From Vehicle_Information.csv:
**make, model, Propulsion_Code**  

Also, the Accidents dataset ranges from year 2005 to 2017, while the Vehicle dataset ranges from 2004 to 2016. Therefore, the rows in the Accidents data where `year == 2017` are eliminated, while the Vehicles data are cleared of the rows with `year == 2004`.

### Removing "Data missing or out of range"
After the first step of cleaning data (removing the unwanted columns and years where no intersection exists between the two datasets), an evaluation on the available data is realised to check the frequency of null values (or, as stated in the datasets, Data missing or out of range). If a column contains significant amounts of null values, these have to be removed in order to not compromise the analysis.



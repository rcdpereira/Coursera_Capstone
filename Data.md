# 2. DATA EVALUATION

## 2.1 Extracting the Data

The dataset for the UK road accidents was obtained from the following source: [UK Road Safety Accidents and Vehicles](https://www.kaggle.com/tsiaras/uk-road-safety-accidents-and-vehicles).
There are two available datasets: Accident_Information and Vehicle_Information. A full metadata was not available.

The source describes both data:
* Accident_Information.csv: every line in the file represents a unique traffic accident (identified by the AccidentIndex column), featuring various properties related to the accident as columns. Date range: 2005-2017.
* Vehicle_Information.csv: every line in the file represents the involvement of a unique vehicle in a unique traffic accident, featuring various vehicle and passenger properties as columns. Date range: 2004-2016.
The datasets can be merged together through the accident identifier (Accident_Index).

## 2.2 Cleaning Data

### 2.2.1 Dropping Features
A thorough evaluation shall be conducted in order to define which features seem to influence the accidents severity. This evaluation is detailed in the Jupyter Notebook where the analysis was performed. For more details, [click here](https://github.com/rcdpereira/Coursera_Capstone/blob/main/Capstone_Project.ipynb) to see the notebook.

### 2.2.2 Merging the Dataframes
The final dataframe called `road_accidents` is assembled after removing the unwanted features and merging the two original dataframes by the `Accident_Index` column. The features are:

 |Table 1:           |`road_accidents` dataframe features |                     |                        |
 |:---               |:---                                |:---                 |:---                    | 
 |Accident_Index     |Accident_Severity                   |Date                 |Day_of_Week             |
 |Junction_Detail    |Light_Conditions                    |Number_of_Vehicles   |Road_Surface_Conditions |
 |Road_Type          |Speed_limit                         |Time                 |Urban_or_Rural_Area     |
 |Weather_Conditions |Age_Band_of_Driver                  |Junction_Location    |Sex_of_Driver           |
 |Vehicle_Manoeuvre  |X1st_Point_of_Impact                |Year                 |                        |


### 2.2.3 Dropping Rows: Missing Data
After the first step of cleaning data and merging the dataframes, an evaluation on the available data is realised to check the frequency of null values (or, as stated in the datasets, Data missing or out of range). This data shall only be removed if the remaining amount of data is still sufficient for performing an analysis. The results are as follow:
> Number of lines in the dataframe:  1389724
>
> Max amount of lines to be dropped:  150428
>
> Max percentage of the data that will be lost:  10.8%
>
>Number of lines remaining after dropping:  1239296

The remaining amount of data seems sufficiently good for generating a model to predict accident severity.

## 2.3 Understanding the Data

An evaluation of each feature is crucial to understand the impacts they may have in the accidents severity. This section presents the final selected features, showing the information each one can provide and explaining why they were selected for prediction.

### Day_of_Week

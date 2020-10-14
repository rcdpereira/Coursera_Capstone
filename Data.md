# 2. DATA EVALUATION

## 2.1 Extracting the Data

The dataset for the UK road accidents was obtained from Kaggle at [UK Road Safety Accidents and Vehicles](https://www.kaggle.com/tsiaras/uk-road-safety-accidents-and-vehicles).
There are two available datasets: Accident_Information and Vehicle_Information. There was not provided a description of the contents in each column.

The source describes both data:
* Accident_Information.csv: every line in the file represents a unique traffic accident (identified by the AccidentIndex column), featuring various properties related to the accident as columns. Date range: 2005-2017.
* Vehicle_Information.csv: every line in the file represents the involvement of a unique vehicle in a unique traffic accident, featuring various vehicle and passenger properties as columns. Date range: 2004-2016.
The datasets can be merged together through the accident identifier (Accident_Index).

## 2.2 Cleaning Data

### 2.2.1 Dropping Features
A thorough evaluation shall be conducted in order to define which features seem to influence the accidents severity, since there is no description about the values from each column. This evaluation is detailed in the Jupyter Notebook where the analysis was performed. To see the noteboook for more details, [click here](https://github.com/rcdpereira/Coursera_Capstone/blob/main/Capstone_Project.ipynb).

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
>Max amount of lines to be dropped:  176127
>
>Max percentage of the data that will be lost:  12.7%
>
>Minimum number of lines remaining after dropping:  1213597

The remaining amount of data seems sufficiently good for generating a model to predict accident severity.

## 2.3 Understanding the Data

This section presents a brief descroption about each feature and why they should be considered as a predictor for an accident severity.

**Date:** can be used to evaluate if accidents are decreasing or increasing over time, and check if there is a specific month where accidents happen more often. Although not directly influencing the severity, the more accidents you have, the higher probability of having fatal and serious ones.

**Day_of_Week:** Fridays are known for the happy hour after work. That may lead to more drunk drivers, and increasing the chances of accidents.

**Junction_Detail:** Crossroads or roundabouts? Which type of junction poses a higher risk? Are the accidents more serious on slip roads, or at T/staggered junctions? THis information can lead to where the drivers attention should be higher.

**Light_Conditions:** The majority of the accidents happen in daylight conditions. But is the severity more concentrated in these daylight accidents? Or maybe it is concentrated in the ones that happened at darkness. Seems interesting to evaluate.

**Number_of_Vehicles:** When more vehicles are involved, is the severity of the accidents increased? Or no correlation exists? Let's find out (in the next section).

**Road_Surface_Conditions:** It's clear that road conditions can increase accidents and the severity. Have you ever tried to drive under a heavy snow storm? Big chances you are gonna crash.

**Road_Type:** Single for dual carriageways pose more risk to those involved in the accident? If slip roads are a bigger threat, you should avoid using the highways whenever possible. Right?

**Spped_limit:** The big villain. It self explanatory why this should be here. Next!

**Time:** Put together with Fridays, the happy hour is after 17:00. The biggest chances to find a drunk driver. Are you going to take it? Or can I convince you to prepare to leave early?

**Urban_or_Rural_Area:** You may think that of course urban areas have more accidents. You''l be surprised. Let me show these results because they are worth it.
> Urban: 785346
>
> Rural: 474447

Wow, as expected urban areas have higher amount of accidents. But did you really expected so much accidents in rural areas? And if you don't, your attention may be lower on these area and the severity of an accident can be higher. So let's keep it for the sake of curiosity.

**Weather_Conditions:** This one is tricky. Let's look at the distribution to see why.
|Weather Condition      |# Accidents|
|:---                   |---:       |
|Fine no high winds     |    1028274|
|Raining no high winds  |     152718|
|Other                  |      26395|
|Raining + high winds   |      18367|
|Fine + high winds      |      16317|
|Snowing no high winds  |       8856|
|Fog or mist            |       7180|
|Snowing + high winds   |       1686|
Yeah, most of the accidents will fall under "Fine no high winds". Maybe this one needs a separate analysis removing those 1,028,274 lines. It's still 231,519 data to infer from. Some good can come out of it.

**Age_Band_of_Driver:** Some rental car companies doesn't allow people under 25 years old to rent a car. Are they really the more risky group of drivers? Or are they the ones involved in the most fatal accidents? Lot's of questions that need answer!

**Junction_Location:** This one seems that can be dropped. It's very similar from Junction_Detail, but the latest seems more interesting. Bye bye!

**Sex_of_Driver:** Are women really terrible drivers as the misoginist jokes point out for years? Or is this just men trying to defend themselves against human beings more careful than them?

**Vehicle_Manoeuvre:** Is the type of manoeuvre an influencer in the severity of accidents? SHould you pay more attention in U-turns?

**X1st_Point_of_Impact:** THis will allow us to determine if some types of collision lead to more severe accidents than others.

**Year:** Maintained for analysing historical trends. Should be removed from the predictive model.

Now that you understand which and why the data was considered to generate a predictive model for accidents severity, it is time to start modelling.

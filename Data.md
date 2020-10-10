# Data Evaluation

The dataset for the UK road accidents was obtained from the following source: [UK Road Safety Accidents and Vehicles](https://www.kaggle.com/tsiaras/uk-road-safety-accidents-and-vehicles).
There are two available datasets: Accident_Information and Vehicle_Information.

The source describes both data:
* Accident_Information.csv: every line in the file represents a unique traffic accident (identified by the AccidentIndex column), featuring various properties related to the accident as columns. Date range: 2005-2017.
* Vehicle_Information.csv: every line in the file represents the involvement of a unique vehicle in a unique traffic accident, featuring various vehicle and passenger properties as columns. Date range: 2004-2016.
The datasets can be merged together through the accident identifier (Accident_Index).

The datasets are loaded as dataframes in a Jupyter Notebook, and some previous evaluations are conducted.


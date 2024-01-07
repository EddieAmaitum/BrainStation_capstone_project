# Taxi Demand Prediction

<img src="https://github.com/EddieAmaitum/Capstone_project/blob/main/Taxi%20demand%20image.png" alt=" photo" width="75%">

## Table of Contents

## [1. Project Overview](#1.-Project-Overview)
### [1.1 Introduction](#1.1-Introduction)
### [1.2 Solution](#1.2-Solution)
### [1.3 Project Impact](#1.3-Project-Impact)
### [1.4 Data Dictionary](#1.4-Data-Dictionary)
### [1.5 Solution Approach](#1.5-Solution-Approach)

## [2. Data Preparation and Exploration](#2.-Data-Preparation-and-Exploration)
### [2.1 Loading Libraries](#2.1-Loading-Libraries)
### [2.2 Loading, Exploring, and Validating the Data](#2.2-Loading,-Exploring,-and-Validating-the-Data)
### [2.3 Transforming Raw Data into Time Series Data for Our Analysis](#2.3-Transforming-Raw-Data-into-Time-Series-Data-for-Our-Analysis)
### [2.4 Transforming the Time Series Data into Tabular Data for Model Training](#2.4-Transforming-the-Time-Series-Data-into-Tabular-Data-for-Model-Training)

## [3. Modeling](#3.-Modeling)
### [3.1 Visualizing Data for Modeling](#3.1-Visualizing-Data-for-Modeling)
### [3.2 Splitting the Data](#3.2-Splitting-the-Data)
### [3.3 Baseline Model 1](#3.3-Baseline-Model-1)
#### [3.3.1 Evaluating Baseline Model 1](#3.3.1-Evaluating-Baseline-Model-1)
### [3.4 Baseline Model 2](#3.4-Baseline-Model-2)
#### [3.4.1 Evaluating Baseline Model 2](#3.4.1-Evaluating-Baseline-Model-2)
### [3.5 Baseline Model 3](#3.5-Baseline-Model-3)
#### [3.5.1 Evaluating Baseline Model 3](#3.5.1-Evaluating-Baseline-Model-3)

## [4. Conclusion](#4.-Conclusion)

## [5. Next Steps](#5.-Next-Steps)

## 1. Project overview

### 1.1 Introduction

**Demand in the taxi and Car share service industry**

* In order for Ride sharing companies like Uber to maximize revenue and improve customer satisfaction, one challenge they must address is taxi delays.
* They must ensure that enough drivers (supply) are readily available to service customers (demand) at all times.
* Companies therefore need to forecast demand.
   
### 1.2 Solution
* My aim in this project is to use machine learning to a build a model that `predicts taxi demand per hour by location`.
* This way drivers can be allocated to high demand areas an peak times and reallocated when demand falls thus maximizing efficiency.
* Using push notifications the drivers can be incentivized to go to specific locations. 
  
### 1.3 Project Impact 
* Predictive models like this one have been shown to cut wait times by up tp 20%.
* Improved efficiency in driver deployment hence companies can generate more revenue.
* Increased customer satisfaction due to enhanced service reliability.

### 1.4 Data Dictionary
I will use the [NYC Taxi & Limousine Commission (TLC) Trip Records](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page) dataset.
*  The NYC TLC website offers an extensive set of monthly taxi trip data, encompassing various records from 2009 to present day.
*  The official [data dictionary](https://www.nyc.gov/assets/tlc/downloads/pdf/data_dictionary_trip_records_yellow.pdf) can be found [here](https://www.nyc.gov/assets/tlc/downloads/pdf/data_dictionary_trip_records_yellow.pdf).
*  In the beginning of our analysis we start with `2022 January yellow_trip` data, as we progress we add more data to build a robust model.
*  Below are the descriptions of the columns:

| Field Name | Description |
|:-----------|:------------|
| VendorID | A code indicating the TPEP provider that provided the record. <br> 1= Creative Mobile Technologies, LLC; 2= VeriFone Inc. |
| tpep_pickup_datetime | The date and time when the meter was engaged. |
| tpep_dropoff_datetime | The date and time when the meter was disengaged. |
| Passenger_count | The number of passengers in the vehicle. <br> This is a driver-entered value. |
| Trip_distance | The elapsed trip distance in miles reported by the taximeter. |
| PULocationID | TLC Taxi Zone in which the taximeter was engaged |
| DOLocationID | TLC Taxi Zone in which the taximeter was disengaged |
| RateCodeID | The final rate code in effect at the end of the trip. <br> 1= Standard rate <br> 2=JFK <br> 3=Newark <br> 4=Nassau or Westchester <br> 5=Negotiated fare <br> 6=Group ride |
| Store_and_fwd_flag | This flag indicates whether the trip record was held in vehicle memory before sending to the vendor, aka “store and forward,” because the vehicle did not have a connection to the server. <br> Y= store and forward trip <br> N= not a store and forward trip |
| Payment_type | A numeric code signifying how the passenger paid for the trip. <br> 1= Credit card <br> 2= Cash <br> 3= No charge <br> 4= Dispute <br> 5= Unknown <br> 6= Voided trip |
| Fare_amount | The time-and-distance fare calculated by the meter. |
| Extra | Miscellaneous extras and surcharges. Currently, this only includes the $0.50 and $1 rush hour and overnight charges. |
| MTA_tax | $0.50 MTA tax that is automatically triggered based on the metered rate in use. |
| Improvement_surcharge | $0.30 improvement surcharge assessed trips at the flag drop. The improvement surcharge began being levied in 2015. |
| Tip_amount | Tip amount – This field is automatically populated for credit card tips. Cash tips are not included. |
| Tolls_amount | Total amount of all tolls paid in trip. |
| Total_amount | The total amount charged to passengers. Does not include cash tips. |
| Congestion_Surcharge | Total amount collected in trip for NYS congestion surcharge. |
| Airport_fee | $1.25 for pick up only at LaGuardia and Jo |

* The dataset was relatively clean.
* I spent a good amount of my time doing feature engineering.

### 1.5 Solution approach
* `Set up the working environment`: I use poetry, conda, VSCode, Git/GitHub as development tools.
* `Data preparation`:
  * I will load raw data from the website, analyze, then transform it for model building using various models.
* `Model training`: I will build baseline models, evaluate their perfomance then iterate to obtain the best performing model.
* `Model operationalization (MLops)`: I hope to build pipelines to deploy the working model.
* `Deploy models` : I hope to build a UI for aundiences to interact with the project.
  
## 4. Conclusion

In this project use time series data to build a model that predicts taxi demand per hour per location.

The dataset used was quite large and relatively clean. I spend some time on feature transformations in preparing the data for modeling.

I built 3 baseline models 2 of which used no machine learning algorithms but logic based on data exploration. The based performing baseline model was xgboost.

I used mean absolute error to evaluate model performance, I will explore other evaluation metrices in the future.

## 5. Next steps

I hope to further improve the model performance, build pipelines to automate process and build a UI for interactivity. I will achieve these by:

1. Increase the training data for example: by adding weather data, by doing further feature engineering.

2. Explore other machine learning algorithms for example LightGBM.

3. Explore more parameters through hyper parameter tuning.

4. Explore evaluation metrices for the models.

5. Build pipelines to automate processes and eliminate redundant steps.

6. Build a UI so that audiences can interact with the project.

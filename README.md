# Taxi Demand Prediction

<img src="https://github.com/EddieAmaitum/Capstone_project/blob/main/Taxi%20demand%20image.png" alt=" photo" width="80%">

## Table of Contents

## [1. Project Overview](#1.-Project-Overview)
### [1.1 Introduction](#1.1-Introduction)
### [1.2 Solution](#1.2-Solution)
### [1.3 Project Impact](#1.3-Project-Impact)
### [1.4 Data Dictionary](#1.4-Data-Dictionary)

## [2 Solution Approach](#2.-Solution-Approach)

## [3. Conclusion](#3.-Conclusion)

## [4. Next Steps](#4.-Next-Steps)

## [5. Appendix](#5.-Appendix)

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

## 2. Solution approach
* `Set up the working environment`: I use poetry, conda, VSCode, Git/GitHub as development tools.
* `Data preparation`:
   * Find this in notebooks 01 - 05.
   * First I fetch raw data from the website and validate.
   * I then analyze the validated data, transform it into time series data and finally tabular data for model building.
* `Model training`:
   * Find this in notebooks 06 - 10.
   * I split the data into train and test sets.
   * I start with building baseline models followed by more robust models.
   * I evaluated model perfomance using Mean Absolute Error(MAE), and iterated to obtain the best performing model.
* `Model operationalization (MLops)`:
   *  I'm continously working to deploy the model as a batch scoring service.
   *  Find this in notebooks 11+, this is an on going proccess.
   *  Here I use [Hopsworks](https://docs.hopsworks.ai/3.5/) as a feature store.
   *  I use github actions to automate model runs.
   * `For model deploment I use [Streamlit](https://streamlit.io/) to build a UI. PS- This is an ongoing process.
  
## 3. Conclusion

In this project I use time series data to build a model that predicts taxi demand per hour per location.

The dataset used was quite large and relatively clean. I spend a good time on feature transformations in preparing the data for modeling.

I built 7 models in total. The based performing model was LightGBM with hyper parameter tuning.

I used mean absolute error to evaluate model performance. See model performance below:

| Model                           | Mean Absolute Error (MAE) | Notes                                   |
|---------------------------------|---------------------------|-----------------------------------------|
| Ad Hoc model 1                  | 6.05                      | Baseline model                          |
| Ad Hoc model 2                  | 3.68                      | Baseline model                          |
| Ad Hoc model 3                  | 3.19                      | Baseline model                          |
| XGBoost                         | 2.70                      | Models improved                         |
| Lightgbm                        | 2.57                      | Models improved                         |
| Lightgbm + feature engineering  | 2.59                      | Added average rides per month           |
| Lightgbm + hyperparameter tuning| 2.54                      | Best model for production (num_leaves, min_child_samples, etc) |


## 4. Next steps

I hope to further improve the model performance by adding more features, build pipelines to automate processes and complete model operationalization.

## 5. Appendix

* Sample streamlit UI dashboard: You can see highlighted high demand areas.
  
<img src="https://github.com/EddieAmaitum/main_capstone_project/blob/main/Streamlit%20App.png" alt=" photo" width="50%">
  

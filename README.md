# Capstone_Project_Engagement_Prediction

## 1. Problem Statement
*Socialinsider* is a social media analytics company that provides data and services for users, like influencers and marketers, to compare performance across channels, get competitor analysis, benchmarks and listening insights. *Socialinsider* is trying to improve their product to gain and retain more customers. The goal of this project is to predict the number of engagement for each profile in order to give users more social media insights. 

## 2. Methods and Data
### 2.1 Benchmark Studies
There's no benchmark studies with similar goal and the data we are using. 
### 2.2 Data
The data we are using to train and test the model is the daily count data of Instagram profiles, spanning from 2023 Jan 1st to 2024 Dec 31st. It contains more than 33 million rows in total. 
### 2.3 EDA

Upon observing the dataset, we have encountered the greatest challenge--discontinuity with lots of missing values—due to the nature of the data collection process. In order to understand these missing values more systematically, we explored the dataset more with stratified layers of profile record counts. The distribution result is demonstrated by the histogram below: 

<img width="718" alt="Screen Shot 2025-04-14 at 5 07 01 PM" src="https://github.com/user-attachments/assets/de00e2a2-d48c-4341-b612-6a01b0bac2ac" />

It can be noticed that most of the profiles have total records of less than 50 days among 366 days (one year data). Only a few profiles have total number of records positioned in the two upper layers, 300-365 days and 366 days. This tilted distribution of the dataset has create obstacles in predicting outcomes with time series models, which prefers continued data. Hence, data preprocessing and resampling has been taken to decrease the sparsity in the data. 

### 2.4 Data Preprocessing
`Resampling: `

An example source data is displayed in this table which has records on a daily basis:

| profile id | date       | followers | post | engagement | reach | impression |
|------------|------------|-----------|------|------------|-------|------------|
| profile 1  | 2024-01-07 | 300       | 0    | 0.0        | 0     | 0          |
| profile 2  | 2024-01-08 | 350       | 1    | 3          | 1     | 2          |

In order to make the dataset less sparse and easier to model, we decided to aggregate the daily data into weekly data where each matrix represent the sum of that value for the entire week. This has significantly decrease the number of null values in the dataset as 7 null values in a week will be aggregated into 1 null value. The resulted aggregated processed table is shown: 

| profile id | date       | followers | post | engagement per post | reach | impression | monthly average engagement per post |
|------------|------------|-----------|------|----------------------|-------|------------|-------------------------------------|
| profile 1  | 2024-01-07 | 300       | 3    | 300                  | 20    | 10         | 500                                 |
| profile 2  | 2024-01-14 | 300       | 2    | 150                  | 50    | 12         | 500                                 |

### 2.5 Modeling
## 3. Results
## 4. Technical Documents
### 4.1 Files Included and How to Replicate
The repo contains the `model_training_pipeline` and `model_prediction_pipeline`. 
- **model training pipeline**

It includes the Jupyter Notebook `engagement_model(1).ipynb` that contains the process to train the model. The output of this file will be 4 exported models and an exported scaler.

To get the training model, get `ig_data-2024` and `ig_data-2023` (not included in this repo due to data size). Put it in the same folder as `engagement_model(1).ipynb`. Run the Jupyter Notebook `engagement_model(1).ipynb`. 

- **model prediction pipeline** It contains: 
    - Example data for 4 months in `ig_data-2024`
    - Models and scalers that will be used in the prediction pipeline in `models` folder
    - The Jupyter Notebook that contains the prediction pipeline in `engagement_model_prediction_pipeline.ipynb`

To get the prediction of engagement for certain account, run the python notebook `engagement_model_prediction_pipeline.ipnyb`. This notebook reads the example data from the folder `ig_data-2024` and load the pretrained models from `models` folder.

For more information about prediction process, go to [here](https://github.com/XueqingWu/Capstone_Project_Engagement_Prediction/tree/main/model_prediction_pipeline)

## 5. Deliverables
The prediction pipeline will be integrated to *Socialinsider*'s website as an API. We will deliver the prediction pipeline (`engagement_model_prediction_pipeline.ipynb`) to our client. 

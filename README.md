# Capstone_Project_Engagement_Prediction

## 1. Problem Statement
*Socialinsider* is a social media analytics company that provides data and services for users, like influencers and marketers, to compare performance across channels, get competitor analysis, benchmarks and listening insights. *Socialinsider* is trying to improve their product to gain and retain more customers. The goal of this project is to predict the number of engagement for each profile in order to give users more social media insights. 

## 2. Methods and Data
### 2.1 Benchmark Studies
There's no benchmark studies with similar goal and the data we are using. 
### 2.2 Data
The data we are using to train and test the model is the daily count data of Instagram profiles, spanning from 2023 Jan 1st to 2024 Dec 31st. It contains more than 33 million rows in total. 
### 2.3 EDA
### 2.4 Data Preprocessing
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
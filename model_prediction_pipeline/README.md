# Model Prediction Pipeline
Prediction Pipeline:
Load Data
Preprocess:
* Sort by date
* convert follower “undefined” to null value
* Drop `likes` and `comments` columns
Feature Engineering:
* Calculate monthly average engagement
Data Transformation:
* Aggregate data by accont and week
    * Create weekly engagement per post 
    * Merge monthly engagement per post 
* Create lag features
* Get the latest row for prediction
* scale the features
Prediction:
* Import Models
* make predictions
* Adjust predictions
    * if the prediction is less than 0, change it to 0
* export table
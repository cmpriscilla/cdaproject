# CDA Spring 2021 Project
Studying the impact of first-order weather variables on rainfall prediction using ML models (Sci-kit Learn) and ARIMAX (PyFlux).

# Description
A commonly proposed way of predicting rainfall is using statistical models on the raw weather data of that day, such as the average temperature, humidity, etc. However, we believe that tomorrow’s weather also depends not only on today’s static weather variables but also the directions of change in today’s weather variables. For example, instead of depending just on the raw temperature of today, tomorrow’s rainfall also depends on whether the temperature is in the trend/seasonality of getting warmer/colder (which may marginally impact the cloud formation). Thus, in comparison to using just the raw weather variables, we hypothesize that using first-order weather data as a proxy of the direction of change for each weather variable would be beneficial in predicting next day’s rainfall. Through this project, we explore the validity of this hypothesis.

# Data Pre-processing
The data were originally drawn from: https://www.kaggle.com/jsphyg/weather-dataset-rattle-package

Since the dataset was collected from many weather stations across Australia, we began by first checking the cities/areas involved in the “Location” column and the amount of data assigned to each of them. Since our aim is to build a general enough model for a certain region of Australia while taking into account the impact of geographical differences and balancing it with the deterring inefficiency of building one specific model for each location, we decided to cluster the cities according to their states/territories and select a state to model for. We decided to choose to focus on the Northern Territory after assessing the quality of the data  that were available for each state/ territory.

There were originally 4 locations identified in the Northern Territory data: Darwin, Alice Springs, Katherine, and Uluru. After careful analysis of the quality of data for each location (such as the amount of data, missing vs available data, possibility of imputing missing data), we decided to drop the data from Uluru.

We also performed further feature selection and engineering to avoid multicollinearity issues.

# Methodology
To assess the hypothesis, we used 3 approaches of modelling as our methods:
1. Non-time series ML models using only the raw weather variables
2. Non-time series ML models using the raw and first-order weather variables
3. ARIMAX models (time-series ARIMA model + exogenous variables linear regression) comparing raw variables only vs raw and first-order variables as the predictor variables.
For each method, we tuned and selected the best model, and their prediction results were in turn compared with each other.

# Conclusion
We proposed a hypothesis that using first-order variables as a proxy of the directions of weather changes would be beneficial in predicting the next day’s rainfall. After exploration and assessment, our results and analysis suggest that this hypothesis only holds true when applied to a time-series model and when we combine the first-order variables with some other raw variables, not as a standalone. Adding the first-order variables may bring in mixed positive and negative impacts in the predictive performance of a non-time-series model.

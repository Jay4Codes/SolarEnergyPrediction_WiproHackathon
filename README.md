# Wipro-Hackathon
Wipro Hackathon
  A solar power generation company wants to optimize solar power production and needs the prediction model to predict ‘Clearsky DHI’, ‘Clearsky DNI’, ‘Clearsky GHI’. The data is     ten years at an interval of every 30 mins with the following data points:

EDA
  Checked for duplicates and NA values, found none.
  GHI = DNI*cos(Zenith-Angle) + DHI
  Using Pearson's correlation visualized a heatmap that showed relationship between all Features.
  So GHI, DNI, DHI had high correlation with Relative Humidity & Solar Zenith Angle. Moderate Correlation with Hour, Temperature & Wind Speed. Temperature has high correlation       with Precipitable Water. Precipitable Water has High correlation with Dew Point.
  Made a separate column to store date instead of 5 columns of Minute, Hour, Day, Month and Year
  Date = pd.to_datetime(df[['Year', 'Month', 'Day', 'Hour', 'Minute']])
  Plotted the data for GHI over time and found yearly seasonality and trends in data

ML
  Initially performed regressions using diff models 
  train_test_split in 80% to 20% ratio
  Linear Regressor, ExtraTrees, DecisionTrees, XGBRegressor
  Where
  ExtraTrees and XGBRegressor performed the best

  Since the validation and train accuracy was less variate and had low mean squared errors, I chose XGBRegressor as the final regressor.
  The training and validation data was split in 9:1 ratio.
  Hyperparameters :- learning_rate = 0.4, max_depth = 9, n_estimators = 1000, reg_alpha = 0

Final Submission
  Found a few negative predicted values in the prediction
  So, converted them to 0.
  Final submission = submission.csv

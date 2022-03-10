# Wipro-Hackathon
<b>Wipro Hackathon</b><br>
  A solar power generation company wants to optimize solar power production and needs the prediction model to predict ‘Clearsky DHI’, ‘Clearsky DNI’, ‘Clearsky GHI’. The data was     ten years at an interval of every 30 mins.<br>

<b>EDA</b><br>
  Checked for duplicates and NA values, found none. <br>
  GHI = DNI*cos(Zenith-Angle) + DHI.<br>
  Using Pearson's correlation visualized a heatmap that showed relationship between all Features. <br>
  So GHI, DNI, DHI had high correlation with Relative Humidity & Solar Zenith Angle. Moderate Correlation with Hour, Temperature & Wind Speed. Temperature has high correlation       with Precipitable Water. Precipitable Water has High correlation with Dew Point. <br>
  Made a separate column to store date instead of 5 columns of Minute, Hour, Day, Month and Year<br>
  Date = pd.to_datetime(df[['Year', 'Month', 'Day', 'Hour', 'Minute']]). <br>
  Plotted the data for GHI over time and found yearly seasonality and trends in data.  <br>

<b>ML</b><br>
  Initially performed regressions using diff models.  <br>
  train_test_split in 80% to 20% ratio. <br>
  Linear Regressor, ExtraTrees, DecisionTrees, XGBRegressor. <br>
  Where ExtraTrees and XGBRegressor performed the best<br>
<br>
  Since the validation and train accuracy was less variate and had low mean squared errors, I chose XGBRegressor as the final regressor. <br>
  The training and validation data was split in 9:1 ratio. <br>
  Hyperparameters :- learning_rate = 0.4, max_depth = 9, n_estimators = 1000, reg_alpha = 0<br>

<b>Final Submission</b><br>
  Found a few negative predicted values in the prediction<br>
  So, converted them to 0.<br>
  Final submission = submission.csv<br>

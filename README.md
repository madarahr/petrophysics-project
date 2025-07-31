# petrophysics-project
Petrophysical analysis to derive formation tops using regression techniques

# Project Overview

This project applies petrophysical analysis techniques to predict depths of formation (rock) tops in the subsurface using data from offset hydrocarbon Wells within the same hydrocarbon field. Formation tops are depth markers that indicate the boundaries between key geological formations. Accurately predicting these tops improves well placement, reduces drilling uncertainty, and enhances subsurface understanding.

The data is from an Oil & Gas field that belongs to a large company. This data is used for training purposes only and it is hence shared with many other companies.

The original intent was to use Well log responses (e.g., gamma ray, resistivity, density, neutron porosity) from offset Wells and identify patterns to predict formation tops and their depths using regression models and apply it to drill a new Well.  Despite having multiple log types, there are some rocks require more analysis to idenity them and this data is limited.  However, the offset Wells have an established analysis of their subsurface rock formations and have associated depths established.  This data from all the Wells was used to predict the formation top depths at a different location in the same field.

<img width="1118" height="600" alt="wellplotGlobal" src="https://github.com/user-attachments/assets/e8c2b984-5721-4bcd-93ea-b68fd1a9b072" />

<img width="1118" height="600" alt="wellPlotLocal" src="https://github.com/user-attachments/assets/48e90e3c-256e-4e7a-ae5e-0ebee1903e25" />

<img width="1218" height="650" alt="wellPlotField" src="https://github.com/user-attachments/assets/eeebc862-e1ad-41f2-93eb-0addaea496da" />



# Objectives

- Integrate well log data from multiple offset wells in a consistent format.

- Perform exploratory data analysis (EDA) to understand relationships between logs and formation tops.

- Train regression models to predict the depth of formation tops in new wells.

- Visualize predictions and assess model performance.

- Test the best performing model against a New Well location

- Provide an interpretable, reproducible workflow for subsurface teams.

# Dataset Description

- Source: Training data used for a petrophysical analysis software called Aspen Geolog
- Type of data:  *.las files and *.txt files
- Data used:
  - Total vertical depth
  - Cartesian grid coordinates
  - Gamma Ray
  - Resistivity
  - Acoustic logs
  - Neutron Porosity
  - Formation top names and corresponding vertical depth

# Technologies & Libraries Used

- pandas, numpy – data handling
- matplotlib, seaborn – visualization
- plotly - map visualization
- scikit-learn – regression modeling
- lasio – reading LAS files

# Exploratory Data Analysis (EDA)

- Data Cleaning (handling missing values, data types)
- Plotting of well curves
- Examination of mnemonics and the location inside the .las files

# Why Regression Was Used:

This project uses regression tools because the target variable is continuous rather than categorical.  Predicting the formation top depths based on offset well formation top depths and the geographic locations requires regression tools.

## Justification:
- The objective is to predict or model a numerical value which is the depth at which a particular formation top can be predicted at a particular location in the field.
- Evaluation metrics used include RMSE, MAE, R² score, which are specific to regression tasks.
- Data relationships explored include linear and non-linear correlations, best understood through regression analysis.

# Well Location and Distance from Each Well
<img width="975" height="196" alt="image" src="https://github.com/user-attachments/assets/99770919-2a05-4248-9280-0c0c9e3e952d" />

# Formation Tops DataFrame
<img width="303" height="385" alt="image" src="https://github.com/user-attachments/assets/51952e64-f3fe-4f2b-aff7-ac81fc485d9c" />

# Well Log Information
<img width="642" height="491" alt="image" src="https://github.com/user-attachments/assets/f0fc6793-f56a-4b54-a723-303753889f9d" />


# Project Structure
- petrophysics-project/petrophysics.ipynb (https://github.com/madarahr/petrophysics-project/blob/main/petrophysics.ipynb) # EDA to explore the data and initial selection of the regression model 
- petrophysics-project/formationDepth_prediction.ipynb (https://github.com/madarahr/petrophysics-project/blob/main/formationDepth_prediction.ipynb) # selection of ideal regression model and applying it to test
- data/		# Raw and cleaned datasets
- notebooks/	# Jupyter notebooks for EDA (petrophysics.ipynb) and for final model (formationDepth_prediction.ipynb) use in prediction
- images/	# Saved plots and visualizations
- output/ # .csv files
- README.md  # Project documentation

# Conclusion

The key findings:
- The signature of the well logs are similar to each other which helps to apply ML however, it was easier to derive formation top depths from offset Well analysis where the formation top depths were established.
- The log data is limited and upon examining, it is not clear that the formation tops can be derived directly from the log signatures.  Hence the offset data and the formation top depths were used directly instead without interpreting the log signature.  More data from sampling, cores are necessary to develop a formation top prediction from the log signatures and other data.
- The key features used are cartesian grid location of the Wells in the form or Easting, Northing, Depth, inter-distance between each Well in the field and the Formation Top name.
- Linear Regression, KNeighbors Regressor, Decision Tree Regressor, SVR, Ridge and Random Forest Regressor were tested and the best performing model were LinearRegression and RandomForestRegression with a high R2-Squared score (0.997424 and 0.997325).

<img width="577" height="239" alt="bestRegressionModel" src="https://github.com/user-attachments/assets/007fbd4d-7181-4a0a-9324-880d8d25e19c" />

<img width="572" height="616" alt="coeffDetermination" src="https://github.com/user-attachments/assets/1023a462-58bc-4176-9b16-ea7e9550043f" />


# Next Steps

The next steps are:
- Determine the formation based on the various logs, sampling information, core analysis to create a robust petrophysical analysis
- Apply geological structure with uncertainity as a feature



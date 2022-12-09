# ML-Electricity-Consumption
Predicting electricity consumption: a Machine Learning (MTAT.03.227) course capstone project

## Team
Dmitri Rozgonjuk <br>
Eerik Sven Puudist <br>
Triin Pohla <br>
Andri Hõbemägi <br>

**Project Owner**: Kristjan Eljand

## Project Topic, Relevance, and Goals
- Increases in energy price can seriously disrupt the daily life of people
- Accurate estimation is relevant on individual level
  - Energy bills and household budgeting
- Accurate estimation is relevant on societal/environmental level
  - Revising energy consumption and reducing where possible
  - Reducing ecological footprint
- Our topic: Predicting energy consumption of a household
- Our goals:
  - Educational: Trying out different modeling techniques learned in the course
  - Tangible value: Providing as accurate predictions as possible

## Project Workflow
Below is a high-level overview of our project workflow on which we elaborate further. In general, we decided to try out different methods in modeling the timeseries: (A) the time-invariant modeling approach which treats time-related variables as usual model features (as opposed to time-series), and (2B) the time-series baed approach. While the former utilizes the information gained from features, the latter typically only needs the sequence of target values. Finally, we ensemble the best of the two approaches in order to see if this improves the predictions.

1. Original Dataset
2. Data Preprocessing
3. Modelling
  - Simpler Baselines
  - Non-Time-Series Based Models
  - Time-Series Based Models
  - Ensemble of our Best Models
4. Final Results

### 1. Original Dataset
The data were retrieved from https://www.kaggle.com/competitions/predict-electricity-consumption. Because the link as well as our main Jupyter notebook (<font color='red'> INCLUDE NAME OF NOTEBOOK </font>) include more detailed overview of the datasets, we refer the read to see them.
    
### 2. Data Preprocessing and Augmentation
In order to compute the models in the view of the two modeling approaches (A: non-time-series based; B: time-series models), we first needed to use pre-processing of data. Firstly, for the both models we imputed the marginal amount of missing data in the target feature by using interpolation (imputation with the average of the previous and next value). We also computed a series of autocorrelations to see if it could be useful to use rolling averages across different time intervals. We found that autocorrelations until three timepoints (i.e., three hours) had high enough correlations to be considered useful (i.e., the correlations dropped more drastically). Hence, we also computed rolling averages for two and three hours across the training data set. Finally, we also log-normalized the original imputed targets as well as the targets base don rolling averages.

#### A: Preprocessing for Non-Time-Series Models
Relevant to modeling the target from features, we first extracted different time-based features from the time sequence feature. We extracted the year, month, month of day, day of week (as integers in order), name of the day (categorical variable), weekend variable (yes or no), hour of the day, season (summer, fall, winter, spring). Additionally, we used an external module to fetch all Estonian holidays for the time period. This resulted in two additional features: whether it is a holiday or not, and holiday type.

We also imputed the missing values of three features:
- `snow`: we essentially used a manual version of fill-forward imputation (using the previous value to impute the missing value).
- `prcp`: we used the fill-forward imputation method.
- `coco`: we used the fill-forward imputation method (also converted to a categorical variable).

#### B: Preprocessing for Time-Series Models
As the Kaggle test data are limited to a specific period of time, it may not be fruitful to use the entire time-series for modeling. For instance, it is common that the energy consumption in winter is driven by heating which is seldomly the case in summer. Hence, we included the data of the last months to model time-series.

## Results
- võime kohe algusesse panna ploti, mis võtab kõik kokku
    - A-models (train + Kaggle), B-models (train + Kaggle), ensemble


### The A-Models (Non-Time-Series Based) Approach
We tried several more commonly used algorithms at this stage. These models include Linear Regression, Regularized Regression Models (Lasso, Ridge, Elastic Net) as well as tree-based models (i.e., Decision Tree, Random Forest). Additionally, we tuned the hyperparameters of these models. 

The best result was achieved by ..., MAE(training) = ... and MAE(kaggle test) = ...


### The B-Models (Time-Series Based) Approach
We also used time-series based models like ...

The best result was achieved with ...,  MAE(training) = ... and MAE(kaggle test) = ...


### Ensembling the Best Models
Finally, we bundled together the best models' predictions into an ensemble. The results showed that this approach resulted in a [BETTER/POORER] performance as the best model ...,  MAE(training) = ... and MAE(kaggle test) = ...


## Summary and Conclusions
The best model predicting energy consumption was ... 


<font color = 'red'> Siia lisame koondjoonise, kus on erinevate mudelite meetrikud ja/või Kaggle skoorid (võime need ka samale joonisele lisada)  </font>

<font color = 'red'> Võiks lisada ka joonise parima mudeli ennustustest </font>



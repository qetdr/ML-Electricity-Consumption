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
# Predicting Electricity consumption

## Team
Dmitri Rozgonjuk <br>
Eerik Sven Puudist <br>
Triin Pohla  <br>
Andri Hõbemägi <br>

**Product Owner:** Kristjan Eljand

# Introduction
The present project was a capstone project for the Machine Learning (MTAT.03.227) course. The general aim was to predict a household's energy consumption. A major side goal of our team was to try out different modeling techniques for educational purposes.

## Our Approach
Our general approach is illustrated in Figure 1, and the steps with detailed annotation are completed throughout this notebook.
![](images/ML_project_workflow.png "Figure 1. General Project Workflow")

It is noteworthy that although the process seems to be relatively linear, this is to illustrate the general workflow from data ingestion to Kaggle submission. In reality, the process included several changes on-the-go, since we learned about new methods and techniques during the project. However, for the sake of cohesion, we display the **general** solution within the present notebook. This means that the model goodness metrics should reflect the **relative** goodness (not the metrics achieved throughout the project process). The original models which were used for actual submissions are split between different notebooks which are stored in the `x_old_files` directory. Although those notebooks had differences in some methods (e.g., how train-test split was done, which target variable was used, etc), the present notebook distills the optimal solutions found with those methods. To that end, we found it fruitful to limit the amount of data used for training (using `prophet`, the best MAE scores were obtained when training was done from May 1st 2022), doing the 80-20 train-validation split based on time (i.e., earlier time series were used as training, later/last timeseries as validation), computing the rolling averages for the target variable and using the 3-hour rolling average as the main target feature.

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



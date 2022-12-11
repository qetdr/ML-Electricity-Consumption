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

# Introduction
The present project was a capstone project for the Machine Learning (MTAT.03.227) course. The general aim was to predict a household's energy consumption. A major side goal of our team was to try out different modeling techniques for educational purposes.

## Our Approach
Our general approach is illustrated in Figure 1, and the steps with detailed annotation are completed throughout this notebook.

![Figure 1](https://github.com/qetdr/ML-Electricity-Consumption/blob/main/images/ML_project_workflow.png)

It is noteworthy that although the process seems to be relatively linear, this is to illustrate the general workflow from data ingestion to Kaggle submission. In reality, the process included several changes on-the-go, since we learned about new methods and techniques during the project. However, for the sake of cohesion, we display the **general** solution within the present notebook. This means that the model goodness metrics should reflect the **relative** goodness (not the metrics achieved throughout the project process). The original models which were used for actual submissions are split between different notebooks which are stored in the `x_old_files` directory. Although those notebooks had differences in some methods (e.g., how train-test split was done, which target variable was used, etc), the present notebook distills the optimal solutions found with those methods. To that end, we found it fruitful to limit the amount of data used for training (using `prophet`, the best MAE scores were obtained when training was done from May 1st 2022), doing the 80-20 train-validation split based on time (i.e., earlier time series were used as training, later/last timeseries as validation), computing the rolling averages for the target variable and using the 3-hour rolling average as the main target feature.

## Results
Below, we present the results of our projects. Of note, we display the goodness of general models on training data. Then, we show how our models/their variantions fared off with Kaggle test data reflected by Public and Private Scores.

### Results on Training Data
We tried several more commonly used algorithms. They could be, roughly, divided in two: non-time-series models and time-series models. For the former, we used Linear Regression, Regularized Regression Models (Lasso, Ridge, Elastic Net) as well as Decision Tree and tree-based ensembles (Random Forest, XGBoost). For the time-series modeling, we used the `prophet` module as well as Random Forest Regressor and XGBoost Regressor from the `skforecast` module. Finally, we ensembled the top three regressors (formed new predictions by averaging the predictions of best models).

Of note, we tested out the mentioned solutions in several variations with Kaggle submissions. In this section, we present the findings of the above-mentioned general solutions for relative reference.

Figure 2 shows the performances of models in relation to runtime. It should be noted that for the TOP Ensemble, the runtimes of best models were added together.

--Figure 2

### Reality Check: Kaggle Results



## Summary and Conclusions
The best model predicting energy consumption was ... 

- lesson learned




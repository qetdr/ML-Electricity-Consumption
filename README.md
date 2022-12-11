# ML-Electricity-Consumption
Predicting electricity consumption: a Machine Learning (MTAT.03.227) course capstone project

## Team
Dmitri Rozgonjuk <br>
Eerik Sven Puudist <br>
Triin Pohla <br>
Andri Hõbemägi <br>

**Project Owner**: Kristjan Eljand

## Project Goal
The present project was a capstone project for the Machine Learning (MTAT.03.227) course. The general aim was to predict a household's energy consumption. A major side goal of our team was to try out different modeling techniques for educational purposes.

## Our Approach
Our general approach is illustrated in Figure 1, and the steps with detailed annotation are completed throughout this notebook.

![Figure 1](https://github.com/qetdr/ML-Electricity-Consumption/blob/main/images/ML_project_workflow.png)

It is noteworthy that although the process seems to be relatively linear, this is to illustrate the general workflow from data ingestion to Kaggle submission. In reality, the process included several changes on-the-go, since we learned about new methods and techniques during the project. However, for the sake of cohesion, we display the **general** solution within the present notebook. This means that the model goodness metrics should reflect the **relative** goodness (not the metrics achieved throughout the project process). The original models which were used for actual submissions are split between different notebooks which are stored in the `x_old_files` directory. Although those notebooks had differences in some methods (e.g., how train-test split was done, which target variable was used, etc), the present notebook distills the optimal solutions found with those methods. To that end, we found it fruitful to limit the amount of data used for training (using `prophet`, the best MAE scores were obtained when training was done from May 1st 2022), doing the 80-20 train-validation split based on time (i.e., earlier time series were used as training, later/last timeseries as validation), computing the rolling averages for the target variable and using the 3-hour rolling average as the main target feature.

We also need to note that the present solutions could not be submitted to Kaggle as Late Submissions for testing the goodness of generic solutions. Hence, the models in the 'main.ipynb' notebook should be taken as rleatively indicative, whereas models with annotations in Figure 3 are a selection of some actual submissions.

## Results
Below, we present the results of our projects. Of note, we display the goodness of general models on training data. Then, we show how our models/their variantions fared off with Kaggle test data reflected by Public and Private Scores.

### Results on Training Data
We tried several more commonly used algorithms. They could be, roughly, divided in two: non-time-series models and time-series models. For the former, we used Linear Regression, Regularized Regression Models (Lasso, Ridge, Elastic Net) as well as Decision Tree and tree-based ensembles (Random Forest, XGBoost). For the time-series modeling, we used the `prophet` module as well as Random Forest Regressor and XGBoost Regressor from the `skforecast` module. Finally, we ensembled the top three regressors (formed new predictions by averaging the predictions of best models).

Of note, we tested out the mentioned solutions in several variations with Kaggle submissions. In this section, we present the findings of the above-mentioned general solutions for relative reference.

Figure 2 shows the performances of models in relation to runtime. It should be noted that for the TOP Ensemble, the runtimes of best models were added together.

![Figure 2](https://github.com/qetdr/ML-Electricity-Consumption/blob/main/images/fig2_train_results.png)

The results show that the ensemble of top 3 models has the lowest MAE. Individually, Prophet, XGBoost, and Tuned Random Forest are the best performers.

### Reality Check: Kaggle Results
The results of the model goodness evaluation for Kaggle Public and Private Scores are in Figure 3. 

![Figure 3](https://github.com/qetdr/ML-Electricity-Consumption/blob/main/images/fig3_kaggle_results.png)

Figure 3 shows that Prophet showed the most promise in predicting household energy consumption. Moreover, models that excluded data before May 2022 seemed to perform better than models which used all available data. 

## Summary and Conclusions
Although we deem the predictions not optimal, we do feel that we achieved the educational goal of the project. To that end, there are several lessons learned:
- When working with time-series data, it really does matter how much data is used. Not all data is of equal merit, and the more recent data should be preferred.
- When a specific period is predicted, it is also reasonable to critically consider whether all features are useful. In our case, using snow level as a predictor for energy consumption in August/September in Estonia did not really make sense.
- The results showed that pre-processing the dadta was useful, especially in the case of using rolling average values for the target.
- Although the best model (prophet) showed high promise reflected by its Public Score, the chosen best solution was disappointing. It could be that the `prophet`-approach is very good in predicting near-future, and its performance drops drastically when predicting further timepoints.
- Relatedly, the initial success achieved with the `prophet`-approach somewhat blinded us, inhibiting further exploration for alternative solutions.
- Finally, we also want to mention that the present project focused on predicting the energy consumption of one household. However, it could be that predicting the energy consumption of thousands (or hundreds of thousands) of individuals might be necessary. To that end, it may be fruitful to also keep in mind the runtime as one potential model metric. Our results showed that the models which used more time tended also to have more accurate predictions.

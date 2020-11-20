## Introduction

15 million people in Tanzania live off of less than $1 a day. Most people living there die before they reach 50 years old. A huge part of the population is forced to use contaminated rivers as a water source, leading to a massive amount of water-borne disease.  

The purpose of this model is to accurately predict functional water wells, to support the ability of locals to obtain clean running water.

## Methodology

* Using data from Taarifa and the Tanzanian Ministry of Water, predict which pumps are functional and which don't work at all based on a number of features, some of the key features explored include:
    * Source of water
    * Payment of water well
    * Age of water well
    * Region
    
* Note:  The data was converted into a binary classification project.  "Functional needs repairs" were relabeled as "Functional".

## Exploring the Data

Through rigorous data exploration, the objective was to identify key features which yeilded highest functional percentages in that category. These features would then be grouped together via a binning process as features of high percentage functional.

#### Water Source

The top performing features include: Rainwater harvesting, Spring, River / Lake

![image.png](https://github.com/NickCatalano14/dsc-mod-3-project-v2-1-onl01-dtsc-pt-052620/blob/926ba615ca7cfbad739699199600fa70c57b950e/water_source_bar_chart_1.png?raw=true)


![image.png](https://github.com/NickCatalano14/dsc-mod-3-project-v2-1-onl01-dtsc-pt-052620/blob/926ba615ca7cfbad739699199600fa70c57b950e/water_source_bar_chart_2.png?raw=true)

The water source features will be binned by features with less than 65% functioning wells and greater than 65% function wells, as can be seen by the second bar chart above.  This method of binning helps to drive the feature importance for the model.

#### Payment
Similary to water source, the method of payment greatly influenced the models performance.  It can be noticed from the bar chart below that the following three features have extremely high percentages of functioning wells; Annual, monthly and per bucket.

![image.png](https://github.com/NickCatalano14/dsc-mod-3-project-v2-1-onl01-dtsc-pt-052620/blob/926ba615ca7cfbad739699199600fa70c57b950e/payment_1png.png?raw=true)

![image.png](https://github.com/NickCatalano14/dsc-mod-3-project-v2-1-onl01-dtsc-pt-052620/blob/926ba615ca7cfbad739699199600fa70c57b950e/payment_1.png?raw=true)


The water source features will be binned by features with less than 70% functioning wells and greater than 70% function wells, as can be seen by the second bar chart above.

#### Age
This new feature was created to identify how the age of a water well could indicate the probability of functioning wells.  As the bar chart clearly depicts, there are extremely high percentages of fucntional wells that are newer.  This percent decreases as the age of the well increases.

![image.png](https://github.com/NickCatalano14/dsc-mod-3-project-v2-1-onl01-dtsc-pt-052620/blob/926ba615ca7cfbad739699199600fa70c57b950e/age.png?raw=true)


#### Region
Another important factor to investigate is the location of the water wells.  By plotting the water wells on a map, where green indicated functioning wells, one may notice areas of high density functioning wells.  This is important to help build the model, as specific regions may have outside properties which promote higher functioning wells. Some of these properties may include; poverty levels, geological conditions and even political.

![image.png](https://github.com/NickCatalano14/dsc-mod-3-project-v2-1-onl01-dtsc-pt-052620/blob/926ba615ca7cfbad739699199600fa70c57b950e/region.png?raw=true)


The percentage of functioning wells across the different regions helps to pin point possible feature characteristics that promote functioning wells.  A breakdown of the percent functioning wells by region can be viewed below.  This map will be used to agin bin regions by the color codes below.

![image.png](https://github.com/NickCatalano14/dsc-mod-3-project-v2-1-onl01-dtsc-pt-052620/blob/926ba615ca7cfbad739699199600fa70c57b950e/region_percent.png?raw=true)


## The Model

There are additional features used for the model. These features and the grouping of them are outlines below:

    * age: [5, 10, 15, 20, 30, 40, 60]
    * lga: [0.5,0.65]
    * ward: [0.4, 0.6]
    * payment: [0.6]
    * quantity: [0.6]
    * management: [0.6]
    * source: [0.65]
    * waterpoint: [0.6]
    * region: [0.5, 0.65]
    * district: [0.3, 0.4, 0.6]
    * extraction_type_class:[0.3]
    * population:[1]
    * installer': [0.45]
    * funder: [0.45]
    * water_quality: [0.65]
    
This method of binning these features is to group features of high percentages of functioning water wells into a class that will be used to increase the importance of that feature for predicting functioning wells.

#### XGBOOST Model

The XGBoost Model was used to train the model, the model performed well with the following resoluts:

* Training set score for SVM: 0.838361
* TestinG set score for SVM: 0.825926

#### Confusion Matrix

![image.png](https://github.com/NickCatalano14/dsc-mod-3-project-v2-1-onl01-dtsc-pt-052620/blob/926ba615ca7cfbad739699199600fa70c57b950e/conf_matrix.png?raw=true)


The part to highlight from the confusion matrixs is the recall of the functioning water wells.  A 92% recall for functioning wells indicates that of the functioning wells predicted, 92% of those are functioning.  This is critically important for a life support system such as providing clean water to those needing it.

#### Feature Importance

![image.png](https://github.com/NickCatalano14/dsc-mod-3-project-v2-1-onl01-dtsc-pt-052620/blob/926ba615ca7cfbad739699199600fa70c57b950e/feature_importance.png?raw=true)


## Conclusion

The key top features used to determind if a water well is functional are:
* LGA
* Region
* Payment
* Management
* Population
* Age

## Future Work

#### Improving model accuracy

Introducting external data to the dataset

* City data - Location, population
* Region poverty data
* Natural disaster data - Earthquakes, floors, droughts

#### Multiclassification Model
To provide future finance allocation by predicting timeframes a well may need repair or how to increase the probability of a long lasting water well for future construction projects.










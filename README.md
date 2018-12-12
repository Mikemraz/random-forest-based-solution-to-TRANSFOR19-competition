# A random forest-based Solution to TRANSFOR19 Competition

## Backgrounds of TRANSPOR19
Organized by: ABJ70 Artificial Intelligence and Advanced Computing Applications

Supported by: IEEE ITSS Technical Activities Sub-Committee “Smart Cities and Smart Mobility”

Sponsored by: Didi Chuxing

#### Resources:
- the official github repository of this competition: 
	[github page](https://github.com/TRANSFORABJ70/TRANSFOR19)
- The GPS trace data of Didi drivers:
	[GAIA Open Dataset](https://outreach.didichuxing.com/research/opendata/en/)

## description of our solution
### Problem formulation
First, we formulate this problem as univariate time series prediction. But the task is not like traditional 
univariate time series task because we are not given the date of the prediction target and the information 
(observation data points) of both before and after prediction are provided, for example, the speed of early 
morning (0:00 am - 5:55am) and noon (11:00am - 3:55pm). 

### High-level discription
Three time series (speed from 00:00-6:00, 11:00-16:00, and 21:00-24:00) are set as features, and the direction of the speed also serves as another feature. The model outputs are time series of speed from 6:00-11:00 and 16:00-21:00. Random forest, known as ensemble model, is adopted to map the relation from what we know to the speed of time period we want to predict.

### Pipeline overview
1. extract historical speed of target road from given raw GPS files.
2. missing value imputation.
3. handle outliers.
4. training and validation datasets preparation.
5. Random forest implementation.


### Some visualizations


## Reflections
The main advantages of our model are:

1. Fast to train, easy to deploy.
2. Not like traditional time series prediction models only consider the information beforehand, our model could utilize the information after the time period of predictions, which renders more accurate results. 
3. the direction information is taken into account which helps model utilize speed history of opposite direction.

The limitation is that we do not search for the optimal hyperparameter of random forest due to time constraint, instead, we use default values. In the future, the model could be optimized by hyperparameter search.

## Instructions
This repository is intended to show results of our solution and how we get there. some preprocessing work is done in [our another solution](https://github.com/Mikemraz/knn-based-solution-to-TRANSFOR19-competition) . 
If you want to run our codes, some necessary changes of source code is required, e.g., the path to load data.

## Important files:

1. modelling:
	- 'random forest solution.ipynb'

2. prediction results:
	- 'Predictions_north.csv'
	- 'Predictions_south.csv'
	
3. short report of our proposal
	- 'random forest solution.docx'

## Contact:
**Team RiverHawks** 

- Team leader: 
	
	- Liming Jiang, University of Massachusetts Lowell (Liming_Jiang@student.uml.edu)

- Team members: 
	- Yuanchang Xie, University of Massachusetts Lowell (Yuanchang_Xie@uml.edu)
	- Tingjian Ge, University of Massachusetts Lowell  (ge@cs.uml.edu)
	- Yunpeng Wu, Baidu Inc (wuyunpengbilly@gmail.com)
	- Yan Li, University of Massachusetts Lowell  (Yan_Li1@student.uml.edu)


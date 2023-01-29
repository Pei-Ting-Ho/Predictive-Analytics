# Predictive-Analytics
This notebook explores the topic of temporal information and predictive model, addressing the two commonly encountered problems:
- Features: How to efficiently compute the feature vectors, given that some features are transform primitives and some are aggregation primitives? 
- Validation: How to accurately validate the model predictions, given that we should avoid the risk of using future events to predict past events?    

## Data Preparation
Here, we make use of powerful python package ([Featuretools](https://featuretools.alteryx.com/en/stable/)) to help prepare the DataFrame. 
Once entities, relationships, and optional cutoff timepoints have been configured, we can then run the Deep Feature Synthesis to automatically create the feature matrix.
Some graphical examples are:
- Transform Primitive: 

<img width="629" alt="Screen Shot 2023-01-29 at 18 40 00" src="https://user-images.githubusercontent.com/62037588/215320747-78dbe710-ef2a-46f5-af0b-bbdb35625ba0.png">

- Aggregation Primitive: 

<img width="1040" alt="Screen Shot 2023-01-29 at 18 39 43" src="https://user-images.githubusercontent.com/62037588/215320740-cee11b05-3d0e-4a2e-acb7-37b59c81c5e7.png">

## Model Construction
Here, instead of following the standard approach to randomly split the dataset into TrainSet and TestSet, we should split the temporal data based on time to ensure we are not mixing the past with the future: 
- Past occurrences, which are then used to train the model
- Future outcomes, which are then used to evaluate the model

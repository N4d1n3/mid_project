# mid_project 

# Model Appliaction Documentation

The functions.ipynb file is complementary in order to run the some of the function on mid_project.ipynb. The both files should be in same directory and functions.ipynb called  in mid_project.ipynb

1. Testing our model before making a lot of changes to the original data and transforming it to get an understanding of it 
Steps taken: 
	a) Categorical features > get dummies encoding
	b) normalized both categorical and numerical data using Normalizer
	c) train/test split 75/25
	
Model accuracy: LinearRegression: 0.331
	 			KNeighbors: 0.456

2. Testing our model before making a lot of changes to the original data and transforming it to get an understanding of it 
	a) applied Ordinal Encoding for categorical features 
	b) normalized both categorical and numerical data using Normalizer
	
Model accuracy: LinearRegression: 0.409
	 			KNeighbors: 0.456	

3. Testing our model before making a lot of changes to the original data and transforming it to get an understanding of it 
	a) using OrdinalEncoder for categorical features
	b) used StandardScaler for transformation

Model accuracy: LinearRegression: 0.665
	 			KNeighbors: 0.759	

	
4. Worked on checking the distributions of each numerical columns to adjust it.
	 a) applied log tranformation on selected features to adjust the 	distributions
	 b) had not removed the outliers yet
	 
Model accuracy: LinearRegression: 0.609
	 			KNeighbors: 0.718	 
				
5. Worked on normalization and transformations
	a) applied log transformation and Yeo-Johnson transformation on selected features (based on 	their distribution plots)
	b) applied StandardScaler 
	
Model accuracy: LinearRegression: 0.600
	 			KNeighbors: 0.719
				
5. Checked for multicollinearity and dropped 2 numericals columns ('sqft_above' (0.86), 	'sqft_lot15' (0.92))

Model accuracy: LinearRegression: 0.589
	 			KNeighbors: 0.716
				
				
6. Adjusted the K number from 5 to 8

Model accuracy: LinearRegression: 0.589
	 			KNeighbors: 0.721
				
7. Tested dropping more numerical columns based on VIF output:

	a) used VIF with threshold 50 > get 4 columns, model accuracy score got worse
	b) used VIF with threshold 30 > get 5 columns, model accuracy gets worse (around 0.52)
	c) undo the manual column drop after heatmap, apply VIF on all numericasl (accuracy around 	0.52)
	
8. Adjusted the K number from 8 to 10 and added new model - RandomForestRegressor (removed 	the depth)

Model accuracy: LinearRegression: 0.600
	 			KNeighbors: 0.731
				RandomForestRegressor: 0.855
				
				
9. Adjusted the train/test split to see the impact on the model accuracy, removed outliers
	
	a) assigned 20% of the data as the test set (before it has been 25%)
	b) dropped columns 'sqft_above' (0.86), 'sqft_lot15' (0.92) because of multicollinearity
	c) removed outliers (with multiplication of 3) from 'sqft_lot'
	
Model accuracy: LinearRegression: 0.697
	 			KNeighbors: 0.800
				RandomForestRegressor: 0.892
				
10. Did another round of outlier and feature removal by using different ways of analyzing the features first
	
	a) removed outliers from different features moving on to other steps while playing around with 	multiplication of 1.5, 3, 1 in setting upper and lower limit
	b) dropped more columns because of multicollinearity (using both heatmap but testing out VIF with 	different thresholds: 50, 30, 10)
	
Model accuracy: with each test all model accuracy dropped, so after undoing all the changes model scores were:
				LinearRegression: 0.698
	 			KNeighbors: 0.804
				RandomForestRegressor: 0.888
	

11. Focused on categorical features now
	
	a) used Chi-square test and dropped different amounts of categorical features based on p-values, 	each case lowering total accuracy
	b) tested with only one categirical feature, got 0.62
	
12. Evaluated what we had done so far and came to the conclusion to go back to the start of feature engineering and test adding back columns we originally dropped.

	a) added 'zipcode' back to features
	b) tried with other combinations
	
As, we had reached the accuracy below and exhausted all combinations of model improving methods, we have agreed on this as our final model to avoid overfitting it.

Model accuracy: LinearRegression: 0.704
	 			KNeighbors: 0.13
				RandomForestRegressor: 0.889

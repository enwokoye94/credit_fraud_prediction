# credit_fraud_prediction
Predicting Credit Card Fraud

Given anomolized features and data as a reuslt of a PCA transformation, we have been tasked to predict future fradulant credit card charges.

### Introduction
The data consists of 284,807 records, 28 parameters returned by the PCA transformation, time of the transaction, and the class (whether fradulant or not)
From initial analysis there were no missing values and fraud cases to non fraud cases broke down:
* 492 fraud cases
* 284315 valid cases
* 99.83% more valid cases than fraud cases
  * *large imbalance only ~ .17% of the cases were fraud*

### Procedure
  1. **Scaling**
  Using scikit-learn, due to wide range of our data and outliers, we will use the RobustScaler vs. the other methods.
   * The outliers are not removed however all values are scaled based on percentiles there more generous of outliers. 
  2. **Corelation**
  We looked at the corelation of the paramaters to the class of the transaction (1 being fraud, and 0 being not fraud).
  
 ![Pairwise Correlation to Class](https://github.com/enwokoye94/credit_fraud_prediction/blob/master/images/corr_plot.png?raw=true)
  
  We can observe some Parameters such as V2, V4, V8, V11, V19, V20, V26, V27, seem to have an possitive correlation with fraud. We can see that more in depth when comparing their box plots and distributions (seen below)
  
  ![Violin plot of positively correlated to class](/images/positive_corr.png?raw=true)
  
  3. **T-tests**
  After finding correlations of the componetes with fraud, we check for statistal differences in our postively correlated parameters before modeling, just for piece of mind and to know what the most infuencing factor would be. 
  
  
  4. **Modeling** 
  Using Sklearn's packages we will model 4 Classification models to determine if a transaction was fraud or not. 
   * Logistic Regression
   * Decision Trees
   * K-Nearest Neighbor
   * SVC
   We then evaluate the models using:
   * recall score
   * accuracy score
   * precision score
   * f1 score
   * roc AUC score
   
*Due to to the imblance of classes saw in our EDA notebook we will use the estimator with the highest AUC Score, as the best estimator.*

   5. **Conclusion** 
   ![Table (corr plot) of our models and our evaluation parameters](/images/results_table.png?raw=true)
   
   In conclusion we see that even though KNeighbors Classifier gives us the highest precision score compared to others it has one of the lowest AUC scores. Due to the large imblances of our data, our Decision Tree Classifier will give us more accurate results based on the AUC score being the closest to 1. 

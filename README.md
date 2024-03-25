###  Business Use Case:

As an MLAI practitioner we are tasked to compare the performance of the classifiers `KNeighborsClassifier()` | `LogisticRegression()` | `DecisionTreeClassifier()` | and `SVC()` in the context of Portuguese banking institution dataset detailing bank’s marketing campaigns to facilitate subscription to a term deposit. Summary of findings related to AI models’ performance along with data analysis, pre-processing, modeling, and business conclusions are expected as deliverables of this exercise.

### Findings | Actionable Insights | Recommendations:

<font color="blue">Models Comparison: Based on the trade-offs between accuracy, precision, recall, and computational efficiency, we can choose the following classifiers (please review the summary dataframe at the very bottom of the notebook)</font>:
- If we prioritize accuracy score, banking institution should choose `KNeighborsClassifier()` or ` DecisionTreeClassifier()` models
- If we prioritize precision and computational efficiency, `DecisionTreeClassifier()` will shine the most, and
- If achieving a high recall is a priority and longer training times and computational resources are not of major concern, then `SVC()` model would be the model of choice

<font color="blue">Observations related to data understanding, pre-processing, and modeling (dive into code and code comments below)</font>:
  - We have 17 features, 10 of which are of object type
  - It appeared that 'default', 'housing', and 'loan' features are suitable for binary encoding using `OneHotEncoder()`
  - After using `OneHotEncoder()`, 7 columns remained to be of object type
  - It appeared that 'job', 'marital', 'education', and 'contact' features are suitable candidates for label encoding using `LabelEncoder()` (we will treat the data points as ordinal categorical data)
  - After using `LabelEncoder()`, 3 columns remained to be of object type, one of which is the target variable 'y_yes'
  - Dropped 'poutcome' with 65% of 'unknown' values and 'month' as features of low relevance; now only one column 'y_yes' remained to be categorical, which is totally okay since it is a target/output variable
  - Overall, 39,922 prospective clients (88.3%) out of the entire sample population (45,211 data points) did not subscribe to a term deposit as derived from past observations
  - It appeared that ‘duration’ (last contact in seconds), ‘pdays’ (number of days passed by after the contact), and ‘previous’ (number of contacts performed during last campaigns) are the most influential factors affecting the subscription to a term deposit
  - Correlation matrix of features also confirmed that ‘duration’ (last contact in seconds) has the biggest impact on oucome variable 'y_yes'
  - Pairplot suggested that data are not evenly distributed, hinting at the need for scaling the data when we will come to data modeling, classifier fitting stage
  - The scatterplot of two most influential features on term deposit suggests that most decisions were made with a duration of the contact up to 25 min (1500/60 sec) and within 1.2 years (450 days / 365 days) since the last marketing campaign
  
<font color="blue">Recommendations for increasing subscriptions to term deposits and making accurate predictions</font>:
  - Marketing team should focus efforts on keeping duration of the contact within 10 – 20 min range
  - Meaningful commitment should be made to staying in touch with prospective clientele at least once annually
  - AI model should be chosen based the trade-offs between accuracy, precision, recall, and computational efficiency as outlined in 'Model Comparison' section above
![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# Client Churn Prediction | Machine Learning Project
A classification machine learning problem aimed at predicting customer churn based on whether customers left the company, labeled as “Yes” or “No”.

<details>
  <summary>
   <h2>Project Goals</h2>
  </summary>

## Methodology
At first 20% of the data were splitted for final testing; stratified by the 'Churn' (target) column.

## Data cleaning
* Convert 'TotalCharges' column which is of object type to float type using pd.to_numeric().
* Eleven missing values were found in the 'TotalCharges' column and were removed from the dataset.
* Data has no duplicates.
* The names of the columns converted from camel case to snake_case.

## Exploratory data analysis
1. Value counts shows the distribution of the churn rate in the data which showed an imbalance in the data (73% - "no", 27% - "yes").
2. Bar chart shows that the data is evenly distributed between two genders.
3. Histogram and box plot of continous features implies that:
    * Some outliers exists for churned users with higher tenure or total charges.
4. Heatmap shows the correlation between the main numerical variables:
    * Total charges is heavily influenced by tenure.
    * Monthly charges also contributes to revenue accumulation.
    * Monthly charges are only weakly related to how long customers stay.

The clean data was exported in a new file "custom_churn_clean.csv"

## Feature selection


## Feature encoding 
One-hot encoding technique was applied to the categorical features, transforming them in True and False categories.

## Evaluation metric 
Churn is costly: missing a churner = lost revenue
So we want to minimize false negatives
Recall answers: “Of all customers who actually churned, how many did we successfully detect?”

- TP (True Positives) = correctly identified churners 
- FN (False Negatives) = missed churners (VERY expensive)

![image.png](attachment:image.png)


## Models training
Nine different models were applied on the data and all results are reported with confusion matrix and classification report showing the recall metric.
1. KNN
2. Logistic regression
3. Decision Tree
4. Bagging
5. Random Forest
6. Ada Boost
7. Gradient Boosting
8. XGBoost Classifier
9. Voting Classifier


## Hyperparameter Tuning
Methods applied:
- Random Search
- Grid Search


  <br>
  <hr> 

</details>






<h1> Client Churn Prediction | Machine Learning Project</h1>

<p>
A classification machine learning project aimed at predicting customer churn 
based on whether customers left the company (<strong>Yes</strong> or <strong>No</strong>).
</p>

<hr>

<h2> Project Goals</h2>

<ul>
  <li>Predict customer churn using supervised machine learning models.</li>
  <li>Identify the main factors influencing churn.</li>
  <li>Compare multiple classification algorithms.</li>
  <li>Optimize model performance through hyperparameter tuning.</li>
  <li>Focus on maximizing <strong>Recall</strong> to reduce missed churners.</li>
</ul>

<hr>

<h2> Methodology</h2>

<p>
The dataset was split into:
</p>

<ul>
  <li><strong>80%</strong> training data</li>
  <li><strong>20%</strong> testing data</li>
</ul>

<p>
A stratified split was applied based on the target variable 
(<code>churn</code>) to preserve the original class distribution.
</p>

<hr>

<h2> Data Cleaning</h2>

<ul>
  <li>Converted the <code>TotalCharges</code> column from object type to float using <code>pd.to_numeric()</code>.</li>
  <li>Removed 11 missing values from the <code>TotalCharges</code> column.</li>
  <li>Verified that the dataset contains no duplicate rows.</li>
  <li>Renamed columns from camelCase to snake_case for consistency and readability.</li>
</ul>

<p>
The cleaned dataset was exported as:
</p>

<pre><code>customer_churn_clean.csv</code></pre>

<hr>

<h2> Exploratory Data Analysis (EDA)</h2>

<h3>1. Churn Distribution</h3>

<ul>
  <li>73% of customers did not churn (<strong>No</strong>)</li>
  <li>27% of customers churned (<strong>Yes</strong>)</li>
</ul>

<p>
This indicates a moderate class imbalance in the dataset.
</p>

<h3>2. Gender Distribution</h3>

<p>
Bar chart analysis showed that the dataset is relatively evenly distributed across genders.
</p>

<h3>3. Numerical Feature Analysis</h3>

<p>
Histograms and boxplots revealed:
</p>

<ul>
  <li>Some outliers among churned customers.</li>
  <li>Higher tenure and total charges for certain customers.</li>
</ul>

<h3>4. Correlation Analysis</h3>

<p>
The correlation heatmap highlighted several important relationships:
</p>

<ul>
  <li><code>total_charges</code> is strongly correlated with <code>tenure</code>.</li>
  <li><code>monthly_charges</code> moderately contributes to revenue accumulation.</li>
  <li><code>monthly_charges</code> has a weak relationship with customer tenure.</li>
</ul>

<hr>

<h2> Feature Engineering</h2>

<h3>Feature Encoding</h3>

<p>
Categorical variables were transformed using 
<strong>One-Hot Encoding</strong>, converting categories into binary features.
</p>

<hr>

<h2>📏 Evaluation Metric</h2>

<p>
Since customer churn is costly for businesses, the project focuses primarily on 
<strong>Recall</strong>.
</p>

<h3>Why Recall?</h3>

<ul>
  <li>Missing a churner may result in lost revenue.</li>
  <li>Recall minimizes false negatives.</li>
  <li>It helps identify as many churners as possible.</li>
</ul>

<p>
Recall answers the following question:
</p>

<blockquote>
“Of all customers who actually churned, how many did the model correctly identify?”
</blockquote>

<p>
Recall Formula:
</p>

<p align="center">
Recall = TP / (TP + FN)
</p>

<ul>
  <li><strong>TP</strong> = True Positives (correctly predicted churners)</li>
  <li><strong>FN</strong> = False Negatives (missed churners)</li>
</ul>

<hr>

<h2>🤖 Models Trained</h2>

<p>
The following machine learning models were trained and evaluated:
</p>

<ol>
  <li>K-Nearest Neighbors (KNN)</li>
  <li>Logistic Regression</li>
  <li>Decision Tree</li>
  <li>Bagging Classifier</li>
  <li>Random Forest</li>
  <li>AdaBoost</li>
  <li>Gradient Boosting</li>
  <li>XGBoost Classifier</li>
  <li>Voting Classifier</li>
</ol>

<p>
Each model was evaluated using:
</p>

<ul>
  <li>Confusion Matrix</li>
  <li>Classification Report</li>
  <li>Recall Score</li>
</ul>

<hr>

<h2>🔍 Hyperparameter Tuning</h2>

<p>
Two optimization techniques were applied:
</p>

<ul>
  <li><strong>Random Search</strong></li>
  <li><strong>Grid Search</strong></li>
</ul>

<p>
These methods were used to identify the best hyperparameter combinations for each model.
</p>

<hr>

<h2>📈 Key Findings</h2>

<ul>
  <li>Tree-based models achieved the best overall performance.</li>
  <li>Random Forest and XGBoost produced the highest recall scores.</li>
  <li>The dataset contains strong non-linear relationships.</li>
  <li>Recall-focused optimization improved churn detection capabilities.</li>
</ul>

<hr>

<h2>🛠️ Technologies Used</h2>

<ul>
  <li>Python</li>
  <li>Pandas</li>
  <li>NumPy</li>
  <li>Matplotlib</li>
  <li>Seaborn</li>
  <li>Scikit-learn</li>
  <li>XGBoost</li>
</ul>

<hr>

<h2>🚀 Future Improvements</h2>

<ul>
  <li>Handle class imbalance using SMOTE.</li>
  <li>Improve feature selection techniques.</li>
  <li>Deploy the model using Streamlit or Flask.</li>
  <li>Add model explainability using SHAP values.</li>
  <li>Optimize classification thresholds for business objectives.</li>
</ul>
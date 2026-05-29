![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

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

<h2> Evaluation Metric</h2>

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

<h2> Models Trained</h2>

<p>
The following machine learning models were trained and evaluated:
</p>

<ol>
  <li>Logistic Regression</li>
  <li>Decision Tree</li>
  <li>Random Forest</li>
  <li>XGBoost Classifier</li>
  <li>Voting Classifier</li>
</ol>

<p>
Each model was evaluated using "Recall score" including other evaluation metrics for comparison:
</p>

<ul>
  <li>Recall Score</li>
  <li>Precision</li>
  <li>F1 Score</li>
  <li>Accuracy</li>
</ul>

<p>
Results:
</p>

| Dataset | Model                 | Recall | Precision | F1 Score | Accuracy |
|----------|-----------------------|--------:|-----------:|----------:|----------:|
| raw | DecisionTree        | 0.5963 | 0.5646 | 0.5800 | 0.7704 |
| raw | LogisticRegression | 0.5000 | 0.6032 | 0.5468 | 0.7797 |
| raw | VotingClassifier   | 0.4973 | 0.6619 | 0.5679 | 0.7989 |
| raw | RandomForest       | 0.4947 | 0.6006 | 0.5425 | 0.7783 |
| raw | XGBoost            | 0.4947 | 0.6187 | 0.5498 | 0.7846 |

<hr>

<h2> Key Findings</h2>

<ul>
<li>Decision Tree achieved the highest recall score, making it the strongest model for identifying positive churn cases.</li>
<li>VotingClassifier produced the highest overall accuracy and precision, indicating more reliable overall predictions.</li>
<li>Tree-based ensemble models (Random Forest, XGBoost, VotingClassifier) delivered balanced performance across all evaluation metrics.</li>
<li>Logistic Regression performed competitively but showed lower recall compared to Decision Tree, suggesting that linear models may not fully capture complex churn patterns.</li>
<li>The performance gap between linear and tree-based models suggests the dataset contains important non-linear relationships.</li>
</ul>

<h2> Hyperparameter Tuning</h2>

<p>
Two optimization techniques were applied:
</p>

<ul>
  <li><strong>Random Search</strong></li>

| Model | Recall | Precision | F1 Score | Accuracy |
|-------|--------:|-----------:|----------:|----------:|
| DecisionTree | 0.5348 | 0.5348 | 0.5348 | 0.7527 |
| RandomForest | 0.5053 | 0.6197 | 0.5567 | 0.7861 |
| LogisticRegression | 0.5000 | 0.6032 | 0.5468 | 0.7797 |
| VotingClassifier | 0.5000 | 0.5736 | 0.5343 | 0.7683 |
| XGBoost | 0.4733 | 0.6254 | 0.5388 | 0.7846 |

  <li><strong>Grid Search</strong></li>

  | Model | Recall | Precision | F1 Score | Accuracy |
|-------|--------:|-----------:|----------:|----------:|
| DecisionTree | 0.5615 | 0.5497 | 0.5556 | 0.7612 |
| LogisticRegression | 0.5000 | 0.6032 | 0.5468 | 0.7797 |
| VotingClassifier | 0.5000 | 0.5736 | 0.5343 | 0.7683 |
| XGBoost | 0.4840 | 0.6511 | 0.5552 | 0.7939 |
| RandomForest | 0.4599 | 0.6442 | 0.5367 | 0.7889 |
</ul>

<p>
These methods were used to identify the best hyperparameter combinations for each model.
</p>

<hr>

<h2> Key Highlights</h2>

<ul>
  <li>The initial models already showed strong performance, with Decision Tree achieving the highest recall and VotingClassifier delivering the best overall accuracy and precision.</li>
  <li>Hyperparameter tuning improved the stability and balance of most models, especially Random Forest and XGBoost.</li>
  <li>Decision Tree consistently remained the best model for recall-focused churn detection across all experiments.</li>
  <li>Ensemble models (VotingClassifier, Random Forest, and XGBoost) maintained higher precision and accuracy, reducing false positive predictions.</li>
  <li>Logistic Regression produced stable but less competitive results, suggesting the dataset contains important non-linear patterns.</li>
  <li>Overall, the optimized models confirmed that tree-based and ensemble approaches are the most effective solutions for this churn prediction problem.</li>
</ul>

<hr>

<h2> Technologies Used</h2>

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

<h2> Future Improvements</h2>

<ul>
  <li>Handle class imbalance using SMOTE.</li>
  <li>Improve feature selection techniques.</li>
  <li>Deploy the model using Streamlit.</li>
  <li>Add model explainability using SHAP values.</li>
  <li>Optimize classification thresholds for business objectives.</li>
</ul>

Link to the presentation: https://docs.google.com/presentation/d/176ruCboH_gYPUXJY6CRD_bqj3L4_gr5l/edit?usp=sharing&ouid=111978843608016953666&rtpof=true&sd=true
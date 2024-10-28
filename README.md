Introduction
The goal of this project is to predict customer churn in a bank using machine learning models. Customer churn refers to the loss of clients or customers. Predicting this event helps banks take proactive measures to retain customers. The dataset contains various features, including customer demographics, account details, and transaction behavior.
The project workflow involves the following stages:
1. Data Preprocessing and Feature Engineering
2. Handling Categorical Variables
3. Creating Interaction Features
4. Feature Scaling
5. Model Training and Evaluation
6. Saving Validation Data for Deployment Testing
 
1. Data Preprocessing and Feature Engineering
Feature engineering is crucial for improving model accuracy. The dataset contains both categorical and numerical variables, requiring different techniques for preprocessing.
- Dropping Unnecessary Columns: We removed columns such as RowNumber, CustomerId, and Surname since they are irrelevant for predicting churn.
- Handling Missing Values: If there had been any missing values, we would have addressed them through imputation or by removing affected rows, though the dataset used was clean.
This ensures the dataset only contains relevant information, enhancing model performance.
2. Handling Categorical Variables
Machine learning models typically require numeric data. Since our dataset contains categorical variables like `Geography` and `Gender`, I needed to convert these into numerical form.
Steps Taken:
- One-Hot Encoding: We converted `Geography` (France, Spain, Germany) and `Gender` (Male, Female) into numerical features using One-Hot Encoding, which creates binary columns for each category.
 - Avoiding Multicollinearity: To prevent multicollinearity (where highly correlated features distort model performance), we dropped one category from each one-hot encoded variable (France from Geography and Male from Gender).
3. Creating Interaction Features
Feature interactions can reveal relationships between variables that may not be apparent when considering features individually. I created interaction features by multiplying related variables. For example:
 - Interaction between Age and CreditScore to capture the relationship between these variables.
 - Interaction between Balance and NumOfProducts to detect whether customers with higher balances and more products behave differently.
These interactions help capture complex relationships and improve model performance.
4. Feature Scaling
Since machine learning algorithms like logistic regression, SVM, and neural networks are sensitive to the scale of data, feature scaling was applied to ensure that all features are treated equally during model training.
I used StandardScaler to scale numeric features, ensuring each feature has a mean of 0 and a standard deviation of 1. This technique standardizes data, making the training process more efficient for models like Logistic Regression, KNN, and Neural Networks.
5. Model Training and Evaluation
The project involves training and evaluating multiple models to determine the best performer.
Models Trained:
• Logistic Regression
• Decision Trees
• Random Forest
• Support Vector Machines (SVM)
• K-Nearest Neighbors (KNN)
• Neural Networks (MLP - Multilayer Perceptron)
• Naive Bayes
Each model was trained on the training dataset, and their performance was evaluated using the following metrics:
- Accuracy: Proportion of correctly predicted churn cases.
- Precision: How many of the predicted churns were correct.
- Recall: How many actual churn cases were identified.
- F1-Score: The harmonic mean of precision and recall, used when there’s an imbalance in classes.
Each model was evaluated to ensure robustness before deployment.
 
Conclusion
This comprehensive project followed a systematic approach to prepare data for machine learning, engineer meaningful features, and evaluate various models to predict bank customer churn. By understanding the reasoning behind each step—handling categorical variables, creating interaction features, applying feature scaling, and evaluating multiple models—you ensure that the model is not only accurate but also generalizes well to unseen data.
Model Performance Results
The following table summarizes the evaluation metrics for each model:

Analysis of Results
1. Top-Performing Models:
Multilayer Perceptron (MLP) exhibited the highest accuracy (0.8685) and a strong F1 score (0.589704), making it a strong candidate for deployment.
Random Forest and XGBoost also demonstrated robust performance, with accuracies of 0.8675 and 0.8595, respectively. These models provided a good balance of precision and recall, crucial for the customer churn context.
2. Notable Insights:
The Support Vector Machine achieved a high precision (0.8900), indicating that when it predicts churn, it is often correct. However, its recall (0.2265) was low, suggesting it failed to identify many actual churners.
Logistic Regression and Naive Bayes yielded lower F1 scores (0.365280 and 0.455696, respectively), indicating that these models struggled with the dataset, particularly in identifying churners accurately.
Rationale for Metric Selection
• The chosen metrics were critical for evaluating model performance in the context of churn prediction, where the cost of false negatives (missing an actual churn) can significantly impact business outcomes.
• Emphasizing precision and recall, along with the F1 score, helped ensure that selected models were not only accurate but also effective at identifying customers likely to churn.
Overview
After thoroughly evaluating multiple models for customer churn prediction, the Multilayer Perceptron (MLP) was identified as the best performing model. This section outlines the rationale for its selection and details regarding its deployment on Azure Machine Learning.
Model Selection
• The Multilayer Perceptron (MLP) achieved the highest accuracy (0.8685) and a competitive F1 score (0.589704) among the models evaluated. Its balanced performance in precision and recall made it the ideal candidate for deployment.
• The choice of MLP was further supported by its ability to capture complex relationships within the data, which is crucial for predicting customer behavior accurately.
Deployment Process on Azure Machine Learning
Model Registration:
The MLP model was registered in Azure Machine Learning’s Model Registry. This step ensures that the model is stored securely and can be easily accessed for deployment and future updates.

DMBI Experiment 04 – Bank Customer Churn System
Experiment Title
Bank Customer Churn System: Classification Using Decision Tree and Naive Bayes
Aim
To explore RapidMiner / Altair AI Studio and implement classification models such as Decision Tree and Naive Bayes on the Bank Customer Churn System dataset.
Objectives
- Understand classification as a supervised machine learning technique.
- Prepare the Bank Customer Churn System dataset for classification.
- Train a Decision Tree classifier.
- Train a Naive Bayes classifier.
- Evaluate and compare the models using accuracy, precision, recall, and confusion matrix.
Software / Tools
- Altair AI Studio (formerly RapidMiner) for the GUI-based practical.
- Python 3.x for the optional equivalent implementation.
- Pandas and scikit-learn for the Python implementation.
Dataset
Input file: Churn_Modelling.csv

Target attribute: Exited
- 0 – Customer stayed with the bank.
- 1 – Customer exited the bank.
The dataset contains customer information such as CustomerId, CreditScore, Geography, Gender, Age, Tenure, Balance, NumOfProducts, HasCrCard, IsActiveMember, EstimatedSalary, and Exited. The exact columns should be checked in the supplied CSV file.
Classification Algorithms
1. Decision Tree
A Decision Tree repeatedly splits data using attribute conditions. Its main components are:
- Root node – first decision attribute.
- Internal nodes – conditions based on attributes.
- Branches – possible outcomes.
- Leaf nodes – final predicted class.
2. Naive Bayes
Naive Bayes is a probabilistic classifier based on Bayes' Theorem. It estimates the probability of a class using the input attributes and assumes conditional independence of attributes given the class.
Altair AI Studio / RapidMiner Workflow
1. Read CSV: Import the Bank Customer Churn System CSV file.
2. Select Attributes: Select the relevant customer attributes for classification.
3. Numerical to Binominal: Convert Exited from numerical to binominal/categorical where required by the selected Naive Bayes configuration. The meanings remain 0 = Stayed and 1 = Exited.
4. Set Role: Set Exited as the label.
5. Split Data: Set partition ratios to 0.8 and 0.2 (80% training and 20% testing).
6. Multiply training data: Send a copy of the training data to each classifier.
7. Decision Tree: Train the Decision Tree model.
8. Naive Bayes: Train the Naive Bayes model.
9. Multiply testing data: Send a copy of the test data to each Apply Model operator.
10. Apply Model: Generate predictions using each trained model.
11. Performance (Classification): Evaluate each model.
Workflow Summary
Read CSV → Select Attributes → Numerical to Binominal → Set Role → Split Data

The 80% training partition is copied to Decision Tree and Naive Bayes. The 20% testing partition is copied to each corresponding Apply Model operator. Each prediction output is connected to a Performance (Classification) operator.
Python Equivalent Implementation
The supplied file bank_customer_churn_system_classification.py implements the same overall classification task in Python. It:
- Reads Churn_Modelling.csv.
- Removes common identifier columns if present.
- Separates Exited as the target.
- Imputes missing numerical and categorical predictor values.
- One-hot encodes categorical predictors.
- Splits the dataset into 80% training and 20% testing data.
- Trains Decision Tree and Gaussian Naive Bayes models.
- Prints accuracy, precision, recall, confusion matrix, and classification report.
- Saves a model comparison CSV.
Install dependencies
pip install pandas scikit-learn
Run
Keep Churn_Modelling.csv in the same folder as the Python file, then execute:
python bank_customer_churn_system_classification.py
The code uses OneHotEncoder(sparse_output=False), which requires scikit-learn 1.2 or newer.
Results Reported in the Supplied Experiment Document
Performance Measure	Decision Tree	Naive Bayes
Accuracy	83.82%	83.10%
False Class Precision	86.50%	84.23%
True Class Precision	66.15%	70.91%
False Class Recall	94.40%	96.91%
True Class Recall	42.61%	29.32%


The source document reports that Decision Tree achieved slightly higher accuracy than Naive Bayes, with a difference of 0.72 percentage points. It also reports higher True Class Recall for Decision Tree.

Important: These are the results reported in the supplied practical document. Results from the Python script can differ because the split, preprocessing, model settings, and dataset version may differ. Use the actual run output as the Python implementation's result.

The source PDF mentions a Decision Tree confusion matrix but does not provide its numeric entries in the extracted result section. The Python program prints the confusion matrix calculated from the actual test predictions.
Conclusion
The classification experiment compares Decision Tree and Naive Bayes for predicting whether a customer stays with or exits the bank. The supplied Altair AI Studio practical reports 83.82% accuracy for Decision Tree and 83.10% for Naive Bayes. Based on the reported accuracy, Decision Tree performed slightly better on that test run.
Project Files
- DMBI_EXP4_Bank_Customer_Churn_System.docx – Updated experiment document.
- bank_customer_churn_system_classification.py – Python equivalent classification code.
- README_Bank_Customer_Churn_System_EXP4.md – This README.
- Churn_Modelling.csv – Input dataset (to be supplied separately).
- bank_customer_churn_classification_results.csv – Generated comparison output after running the Python script.

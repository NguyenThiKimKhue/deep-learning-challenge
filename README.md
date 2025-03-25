# deep-learning-challenge
Module 21

Overview
This analysis was developed for Alphabet Soup, a nonprofit foundation seeking to fund organizations with the best chance of success. Using machine learning and neural networks, the goal was to build a binary classifier that predicts whether an organization will be successful if funded. The analysis involved three main phases: data preprocessing, neural network model development (compiling, training, and evaluating), and model optimization.

Key Columns:
•	Target Variable: IS_SUCCESSFUL (indicates the success of an application)
•	Feature Variables: Includes variables such as STATUS, ASK_AMT, various APPLICATION_TYPE_* columns, along with others like ORGANIZATION_Trust and SPECIAL_CONSIDERATIONS_Y.
•	Exclusions: The EIN and NAME columns were excluded during preprocessing as they were deemed irrelevant for modeling.

Data Preprocessing
In this phase, the data was prepared for modeling using Python libraries such as Pandas and scikit-learn. Key preprocessing steps included:
•	Identification of Variables
o	Target Variable: IS_SUCCESSFUL (indicates whether the funding was effectively used).
o	Feature Variables: All other columns after removing identification columns (e.g., APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, STATUS, INCOME_AMT, SPECIAL_CONSIDERATIONS, ASK_AMT).
•	Columns Removed:
o	EIN and NAME were dropped since they do not contribute to the prediction and serve only as identifiers.
•	Data Exploration:
o	Counted unique values for each column to understand the distribution.
o	For columns with more than 10 unique values, the frequency of each unique value was calculated. This helped in identifying rare categorical values.
•	Handling Rare Categories:
o	A cutoff point was established based on the frequency counts, and values that did not meet the threshold were replaced with a new value labeled "Other" to reduce noise and improve model performance.
•	Encoding and Scaling:
o	Categorical variables were encoded using pd.get_dummies().
o	The dataset was split into feature array X and target array y using train_test_split.
o	Data was scaled using scikit-learn’s StandardScaler() by fitting on the training set and then applying the same transformation to the test set.

Model Training and Evaluation:
•	Various attempts were made to enhance the model's performance:
o	Additional columns, including EIN and NAME, were dropped.
o	Binning ranges for the CLASSIFICATION and APPLICATION_TYPE columns were adjusted to group more values (e.g., changing from <1000 to <1500).
o	The number of hidden layers was increased from 2 to 3, and the number of neurons in each layer was modified (e.g., from 100, 40 to 120, 80, 30 and to 300, 100, 10).
o	The number of epochs was reduced from 100 to 50 to save time due to small size.

File Breakdown:
•	Colab file: Charity_byKimNguyen
•	The trained model:  AlphabetSoupCharity.h5
•	Optimized model 1: AlphabetSoupCharity_Optimization2.h5
•	Optimized model 2: AlphabetSoupCharity_Optimization3.h5

Overall Results:
•	The neural network was successfully developed and achieved a predictive accuracy in the target range (75%+), indicating that the model is capable of differentiating between organizations that are likely to succeed or not if funded.
•	The preprocessing steps ensured that noise was reduced by combining rare categorical values and scaling numerical features, which in turn improved model training and performance.

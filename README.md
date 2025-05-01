## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
      import pandas as pd
      df=pd.read_csv("Encoding Data.csv")
      df

  ![image](https://github.com/user-attachments/assets/d975804c-45df-46e8-83b4-863bcd986e63)
  
      from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
      pm=['Hot','Warm','Cold']
      e1=OrdinalEncoder(categories=[pm])
      e1.fit_transform(df[["ord_2"]])

  ![image](https://github.com/user-attachments/assets/1fe3f546-aa13-4a24-a955-cd19f21cbc8c)
  
      df['bo2']=e1.fit_transform(df[["ord_2"]])
      df
      
  ![image](https://github.com/user-attachments/assets/7ec618dd-a934-4dc5-906e-e7e24bc34ab5)

      

# RESULT:
       # INCLUDE YOUR RESULT HERE

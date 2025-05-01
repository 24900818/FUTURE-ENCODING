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

      le=LabelEncoder()
      dfc=df.copy()
      dfc['ord_2']=le.fit_transform(dfc['ord_2'])
      dfc
 ![image](https://github.com/user-attachments/assets/09c0198a-eccd-46a2-8c3d-3e397126b5f0)
 
        from sklearn.preprocessing import OneHotEncoder
        ohe=OneHotEncoder(sparse_output=False)
        df2=df.copy()
        enc=pd.DataFrame(ohe.fit_transform(df2[["nom_0"]]))


       df2=pd.concat([df2,enc],axis=1)
       df2

 ![image](https://github.com/user-attachments/assets/de11795f-a8e2-4414-8d1f-298e2ed65600)

      pd.get_dummies(df2,columns=["nom_0"])
  ![image](https://github.com/user-attachments/assets/989d4989-caf3-46fc-9983-a87d4b573212)
       
      from category_encoders import BinaryEncoder
      df=pd.read_csv("data.csv")
      df



  
      be=BinaryEncoder()
      nd=be.fit_transform(df['Ord_2'])
      df
  ![image](https://github.com/user-attachments/assets/b3ed4a67-864f-4c92-9521-2cc1d95c567a)

      dfb=pd.concat([df,nd],axis=1)
      dfb
  ![image](https://github.com/user-attachments/assets/6dbd119c-f3bc-4ef2-8758-8c690a073e76)
         from category_encoders import TargetEncoder
         te=TargetEncoder()
         CC=df.copy()
         new=te.fit_transform(X=CC["City"],y=CC["Target"])
         CC=pd.concat([CC,new],axis=1)
         CC 
  ![image](https://github.com/user-attachments/assets/e4784643-68d6-41ec-932d-1ea12bf6378c)
         from scipy import stats
         import numpy as np
         df=pd.read_csv("Data_to_Transform.csv")
         df
       
  ![image](https://github.com/user-attachments/assets/f7c38c31-2edd-4881-837d-c8dcf2e3ea0a)
       
         df.skew()
         
  ![image](https://github.com/user-attachments/assets/d370207e-e533-4c54-a804-00b4c3508d7b)
  
         np.log(df["Highly Positive Skew"])
         
  ![image](https://github.com/user-attachments/assets/df32c4a4-3a97-46b0-8bfa-bd322d83c440)

         np.reciprocal(df["Moderate Positive Skew"])
         
  ![image](https://github.com/user-attachments/assets/0264d80d-da88-4513-a739-074ad30b50e9)
       
         np.sqrt(df["Highly Positive Skew"])
         
  ![image](https://github.com/user-attachments/assets/91682c94-f3f4-4c0a-ac2f-fa34ab2ae7d1)
         np.square(df["Highly Positive Skew"])
         
  ![image](https://github.com/user-attachments/assets/4b865ff1-1c51-4ab9-aeee-bf14d3fd194a)
  
         df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])
         df
         
  ![image](https://github.com/user-attachments/assets/fe51401f-f87e-484a-b5c1-c7ee0dbaa25d)
  
         df.skew()
         
  ![image](https://github.com/user-attachments/assets/1f6cc64b-7822-4202-a1ad-4d1854ff4e37)
  
         df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
         df.skew()
         
  ![image](https://github.com/user-attachments/assets/25c02a61-44aa-48ba-aa35-1037cfd51f33)
  
         from sklearn.preprocessing import QuantileTransformer
         qt=QuantileTransformer(output_distribution='normal')
         df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate Negative Skew"]])
         df
         
  ![image](https://github.com/user-attachments/assets/2ea50fa9-1e69-468d-b70e-479123b686ec)

        import seaborn as sns
        import statsmodels.api as sm
        import matplotlib.pyplot as plt
        sm.qqplot(df["Moderate Negative Skew"],line='45')
        plt.show()
        
 ![image](https://github.com/user-attachments/assets/5033d0f1-ed5d-4bce-9f1b-0387964e0ced)
     
      sm.qqplot(df["Moderate Negative Skew"],line='45')
      plt.show()

 ![image](https://github.com/user-attachments/assets/85557efe-c8e5-4380-9d30-9aa5704a0ab0)
       
        from sklearn.preprocessing import QuantileTransformer
        qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)

        df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])

        sm.qqplot(df["Moderate Negative Skew"],line='45')
        plt.show()

  ![image](https://github.com/user-attachments/assets/4c1e5a8b-3fe0-42d6-b8ff-4c7b5035b4ec)

      df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
      sm.qqplot(df["Highly Negative Skew"],line='45')
      plt.show()
      
  ![image](https://github.com/user-attachments/assets/42a6342f-599c-4241-ad79-f174301ccc97)
  
       dt=pd.read_csv("titanic_dataset.csv")
       dt 

  ![image](https://github.com/user-attachments/assets/f98cf4a5-1da5-468a-b8d1-335e371ce24c)
  
       from sklearn.preprocessing import QuantileTransformer
       qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
       dt["Age_1"]=qt.fit_transform(dt[["Age"]])
       sm.qqplot(dt['Age'],line='45') 
       plt.show()
       
  ![image](https://github.com/user-attachments/assets/998836f5-a7f5-4336-87d5-202027af8dfb)
  
       sm.qqplot(df["Highly Negative Skew_1"],line='45')
       plt.show()
       
  ![image](https://github.com/user-attachments/assets/6aa61325-d826-40a4-9cf3-90758069b888)
 
# RESULT:
         Thus the given data, Feature Encoding, Transformation process and save the data to a file was performed successfully.

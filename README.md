# EXNO2DS
# AIM:
      To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT

# Developed by: Eswanth Kumar K
# Register no: 212223040046

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df=pd.read_csv("titanic_dataset.csv")
df
![Screenshot 2025-03-25 103734](https://github.com/user-attachments/assets/1b587366-9ab4-4daf-91b8-3c53d9a65f8f)

df.info()
![Screenshot 2025-03-25 103916](https://github.com/user-attachments/assets/fe612d27-4875-4066-9f8e-65d5806089cf)

df.shape
![Screenshot 2025-03-25 104023](https://github.com/user-attachments/assets/727895db-b55c-404c-a5d1-f8ea135e6363)

df.set_index("PassengerId",inplace=True)
df.describe()
![Screenshot 2025-03-25 104130](https://github.com/user-attachments/assets/85704583-3c32-436c-9ec0-484d38349ba0)

df.shape
![Screenshot 2025-03-25 105550](https://github.com/user-attachments/assets/ca896fb7-9015-4926-a13e-9c88f8990e29)

## Categorical data analysis

df.nunique()
![Screenshot 2025-03-25 105639](https://github.com/user-attachments/assets/deb0e257-4a53-490a-b985-54d8dcb47be2)

df["Survived"].value_counts()
![Screenshot 2025-03-25 105836](https://github.com/user-attachments/assets/69b25316-7e39-47af-b95b-15398d1eda1f)

per=(df["Survived"].value_counts()/df.shape[0]*100).round(2)
per
![Screenshot 2025-03-25 105921](https://github.com/user-attachments/assets/59b7e66e-6db2-445f-a869-df475b367211)

sns.countplot(data=df,x="Survived")
![Screenshot 2025-03-25 110041](https://github.com/user-attachments/assets/7eb792af-f6aa-423a-a88e-f7fe48dce37e)

df
![Screenshot 2025-03-25 110116](https://github.com/user-attachments/assets/a7548b3d-237a-48b4-8698-311e49cc70b7)

df.Pclass.unique()
![Screenshot 2025-03-25 110207](https://github.com/user-attachments/assets/bc23173a-8e09-4b41-86a4-62f81e74c6a7)

df.rename(columns={'Sex':'Gender'},inplace=True)
df
![Screenshot 2025-03-25 110247](https://github.com/user-attachments/assets/c4237ee6-288f-430c-8277-08bbb8e6dba0)


## Bivariate analysis

sns.catplot(x="Gender",col="Survived",kind="count",data=df,height=5,aspect=.7)
![Screenshot 2025-03-25 110345](https://github.com/user-attachments/assets/42fb88c6-0455-44f2-aade-fcdbfa231843)

sns.catplot(x="Survived",hue="Gender",data=df,kind="count")
![Screenshot 2025-03-25 110436](https://github.com/user-attachments/assets/f3e3efaf-52f0-4800-854d-b68770da0379)

df.boxplot(column="Age",by="Survived")
![Screenshot 2025-03-25 110523](https://github.com/user-attachments/assets/88f29b8d-c999-42cc-bc4f-e30c52b9ae6a)

sns.scatterplot(x=df["Age"],y=df["Fare"])
![Screenshot 2025-03-25 110708](https://github.com/user-attachments/assets/d6636eed-39b9-4b8d-9ad1-8b6179f20690)

sns.jointplot(x="Age",y="Fare",data=df)
![Screenshot 2025-03-25 110730](https://github.com/user-attachments/assets/77274b93-8a14-4bfe-8c1b-987d5568115b)

## Multivariate analysis

fig, ax1 = plt.subplots(figsize=(8,5))
plt = sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=df)
![Screenshot 2025-03-25 110823](https://github.com/user-attachments/assets/01a9b209-2711-4e83-848a-f115335eca60)

sns.catplot(data=df,col="Survived",x="Gender",hue="Pclass",kind="count")
![Screenshot 2025-03-25 110905](https://github.com/user-attachments/assets/e1fecde0-7d3f-46b8-9694-999b77e1a6cc)

## Co-relation

corr = df.select_dtypes(include=['number']).corr()
sns.heatmap(corr,annot=True)
![Screenshot 2025-03-25 111641](https://github.com/user-attachments/assets/9414afda-1946-4c86-bdda-e7f0a32e9534)

sns.pairplot(df)
![Screenshot (277)](https://github.com/user-attachments/assets/148da72a-c8f0-436f-864a-276d48ec00c3)



# RESULT:
We have performed Exploratory Data Analysis on the given data set successfully.

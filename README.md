# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them

AIM: TO detect and remove the outliers in the given data set and save the final data.

ALGORITHM

STEP 1
Read the given Data

STEP 2
Get the information about the data

STEP 3
Detect the Outliers using IQR method and Z score

STEP 4
Remove the outliers

STEP 5
Plot the datas using Box Plot

CODE:
(1) & (2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe

```
import pandas as pd
import numpy as np
import seaborn as sns

df = pd.read_csv("/content/drive/MyDrive/Colab Notebooks/Semester 3/19AI403 - Data Science/bhp.csv")
df

df.head()

df.describe()

df.info()

df.isnull().sum()

df.shape

sns.boxplot(x="price_per_sqft",data=df)

q1 = df['price_per_sqft'].quantile(0.25)
q3 = df['price_Aper_sqft'].quantile(0.75)
print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1
ul = q3+1.5*IQR
ll = q1-1.5*IQR

df1 =df[((df['price_per_sqft']>=ll)&(df['price_per_sqft']<=ul))]
df1

df1.shape

sns.boxplot(x="price_per_sqft",data=df1)
```
(3) Examine price_per_sqft column and use zscore of 3 to remove outliers.
```
from scipy import stats

z = np.abs(stats.zscore(df['price_per_sqft']))
df2 = df[(z<3)]
df2

print(df2.shape)
sns.boxplot(x="price_per_sqft",data=df2)
```
(4)(i) For the data set height_weight.csv detect weight outliers using IQR method
```
df3 = pd.read_csv("/content/drive/MyDrive/Colab Notebooks/Semester 3/19AI403 - Data Science/height_weight.csv")
df3

df3.head()

df3.info()

df3.describe()

df3.isnull().sum()

df3.shape

sns.boxplot(x="weight",data=df3)

q1 = df3['weight'].quantile(0.25)
q3 = df3['weight'].quantile(0.75)
print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1
ul = q3+1.5*IQR
ll = q1-1.5*IQR

df4 =df3[((df3['weight']>=ll)&(df3['weight']<=ul))]
df4

df4.shape

sns.boxplot(x="weight",data=df4)
```
OUTPUT :
(1)(2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.

![ds 215](https://user-images.githubusercontent.com/119559844/228053739-a0b3740d-cf62-4584-b880-101799524048.png)

![ds 216](https://user-images.githubusercontent.com/119559844/228055339-cea1e31d-ae83-4ae6-8e62-f5ff7639f3bb.png)

![image](https://user-images.githubusercontent.com/119559844/228056070-8374f4b0-2d84-4b12-b0ff-7c4f84fc2ffa.png)

![df describe ](https://user-images.githubusercontent.com/119559844/229995816-ab529654-edab-4699-b1a4-c6c59d470c59.png)

![sna](https://user-images.githubusercontent.com/119559844/229995907-bdaeeac3-4014-4ee7-b870-341aa42e35f5.png)

![iqr](https://user-images.githubusercontent.com/119559844/229996483-d4504436-7025-4468-b012-b496af8934e0.png)

![shape](https://user-images.githubusercontent.com/119559844/229996530-ffd50beb-b2de-47e3-9161-3b698cd6a49b.png)


(3) Examine price_per_sqft column and use zscore of 3 to remove outliers.

![scipy](https://user-images.githubusercontent.com/119559844/229996998-be5bb2c1-7220-4802-a912-43da389113db.png)

![boxplot](https://user-images.githubusercontent.com/119559844/229997080-4fc5fe66-5378-43fa-bdfe-3d0118773fb6.png)


(4) For the data set height_weight.csv detect weight and height outliers using IQR method

![1](https://user-images.githubusercontent.com/119559844/229998819-9c755c15-ff89-4ec9-a43d-5e3c43860adf.png)

![head](https://user-images.githubusercontent.com/119559844/229998907-dd9160d2-da48-47c7-9adf-49a3ddc22ab3.png)

![describe 1 ](https://user-images.githubusercontent.com/119559844/229999685-c87e7150-3cd6-434c-bf36-7e82b90b5a4b.png)

![sns 1](https://user-images.githubusercontent.com/119559844/230000156-26585ba5-8d8a-443d-b670-eae135f0f8bd.png)

![df4](https://user-images.githubusercontent.com/119559844/230000196-3696ac4b-9860-4659-a4ce-d143c9780986.png)

![df3](https://user-images.githubusercontent.com/119559844/230000996-9a132904-3c96-4f2e-81d1-bb0bd6fc4352.png)

![df5](https://user-images.githubusercontent.com/119559844/230001031-700d8699-d68e-43aa-9357-073ae878b55e.png)

![height](https://user-images.githubusercontent.com/119559844/230001075-b4cb6ba8-c660-439b-a13c-a44a10b5d241.png)



RESULT :

The given datasets are read and outliers are detected and are removed using IQR and z-score methods

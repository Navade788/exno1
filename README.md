# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
import pandas as pd
data=pd.read_csv("/content/SAMPLEIDS.csv")
data
```
![image](https://github.com/user-attachments/assets/3a8b9bc1-dfc3-426a-a03f-916802a2cfdd)
```
data.head(8)
```
![image](https://github.com/user-attachments/assets/865bd9c0-eeb8-4cfa-97c6-6ca5b278cb61)
```
data.tail(10)
```
![image](https://github.com/user-attachments/assets/98fa11e7-29d9-40c2-b5aa-0732a51ef0b0)
```
data.isnull()
```
![image](https://github.com/user-attachments/assets/f720bbf7-9403-4b38-95f3-aed5fe32a826)
```
data.notnull()
```
![image](https://github.com/user-attachments/assets/04f9ed53-a7c4-4e1f-89bd-e149e5635240)
```
data.fillna(5)
```
![image](https://github.com/user-attachments/assets/ec6c202b-cac9-4e10-a58c-aa3af17447f6)
```
data.dropna(axis=0)
```
![image](https://github.com/user-attachments/assets/859df947-f277-4fa1-9b7a-ce5512463d01)
```
data.dropna(axis=1)
```
![image](https://github.com/user-attachments/assets/3aef78ff-9e0b-4fc5-9197-8547fb3c69a0)
```
data.isnull().sum()
```
![image](https://github.com/user-attachments/assets/4b1b2db9-9b2c-4f2f-b747-425088aee690)
```
data.fillna(method='ffill')``
```
![image](https://github.com/user-attachments/assets/83648f10-5ffa-4dec-b64e-3c30263b0a0b)
```
data.fillna(method='bfill')
```
![image](https://github.com/user-attachments/assets/25fe38ea-f6c5-4034-97f5-f2bda7486500)

<h3 align="center">IQR(Inter Quartile Range)</h3>

```py
import pandas as pd
```
```py
ir=pd.read_csv('iris.csv')
ir
```
![image](https://github.com/DHINESH-SEC/exno1/assets/118351569/f6f3cc2e-76cb-4f8f-9239-0ddf27fc1190)

```py
ir.describe()
```
![image](https://github.com/DHINESH-SEC/exno1/assets/118351569/51edfdf6-d999-4cc4-ac15-04bc9594df82)

```py
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/DHINESH-SEC/exno1/assets/118351569/b68ee748-f275-44fe-8cc8-6f19b3e4a386)

```py
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/DHINESH-SEC/exno1/assets/118351569/69d60917-d227-4367-b0ef-ff7ce6e959d8)

```py

rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/DHINESH-SEC/exno1/assets/118351569/57c049f2-3948-4a40-99b2-af0c54f9395d)

```py
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/DHINESH-SEC/exno1/assets/118351569/a1e4026a-3a97-41c7-81c9-92b4ca4997fa)

```py
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/DHINESH-SEC/exno1/assets/118351569/1e19ac51-2803-4a07-9e0b-d7c2b7583882)

<hr><hr>

<h3 align="center">Z-Score</h3>

```py
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
```
```py
dataset=pd.read_csv("heights.csv")
dataset
```
![image](https://github.com/DHINESH-SEC/exno1/assets/118351569/39c53e03-1ea4-4852-b611-cfd529f2596b)

```py
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```

```py
iqr = q3-q1
iqr
```
![image](https://github.com/DHINESH-SEC/exno1/assets/118351569/2d26a119-fec1-4349-a5d8-de847121ab75)

```py
low = q1 - 1.5*iqr
low
```
![image](https://github.com/DHINESH-SEC/exno1/assets/118351569/79354921-d9ba-439f-877f-592a0a4ce18e)

```py
high = q3 + 1.5*iqr
high
```
![image](https://github.com/DHINESH-SEC/exno1/assets/118351569/cc3cb025-3fef-4ce6-aa06-4f955c68c37b)


```py
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/DHINESH-SEC/exno1/assets/118351569/98644856-3b03-4f58-b361-75be46820c24)

```py
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/DHINESH-SEC/exno1/assets/118351569/fa7b418c-9efb-4118-9a21-7f271d0fb1d5)

```py
df1 = df[z<3]
df1
```
![image](https://github.com/DHINESH-SEC/exno1/assets/118351569/08be1792-3872-4f44-922f-ff50c606b79e)






















            
# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.

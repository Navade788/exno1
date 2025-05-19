# NAME :
S.NAVADEEP
# REGD NO.:
212224230180


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
            <<include your coding and its corressponding output screen shots here>>
```
import pandas as pd
data = pd.read_csv("/content/Data_set.csv")
data
```

![Screenshot 2025-03-04 110014](https://github.com/user-attachments/assets/9b43de83-e42b-4ab5-8438-9511fcc1ff63)

```
import pandas as pd
data = pd.read_csv("/content/Data_set.csv")
data.head()

```
![image](https://github.com/user-attachments/assets/69db19a5-e753-4a68-84c8-4c6435eb72cd)
```
import pandas as pd
data = pd.read_csv("/content/Data_set.csv")
data.tail()
```
![image](https://github.com/user-attachments/assets/ff3b22e5-619a-495b-a298-855bd5800df9)
```
import pandas as pd
data = pd.read_csv("/content/Data_set.csv")
data.isnull()
```
![image](https://github.com/user-attachments/assets/e4d1774d-50d3-45ef-b18d-2b1719b1511c)
```
import pandas as pd
data = pd.read_csv("/content/Data_set.csv")
data.notnull()
```
![image](https://github.com/user-attachments/assets/646a80ef-fcf8-40a3-bf07-e1c893c59713)
```
import pandas as pd
data = pd.read_csv("/content/Data_set.csv")
data.fillna(400)
```
![image](https://github.com/user-attachments/assets/45c1c8c6-9d43-45bc-9c47-5842f5bbc94d)
```
import pandas as pd
data = pd.read_csv("/content/Data_set.csv")
data.dropna(axis = 1)
```
![image](https://github.com/user-attachments/assets/a35545ee-0a4d-49f9-9720-65ec61a27f37)
```
import pandas as pd
data = pd.read_csv("/content/Data_set.csv")
data.shape
```
![image](https://github.com/user-attachments/assets/e126fc55-ee44-42a1-9b39-b3cf7d08ad40)
```
import pandas as pd
data = pd.read_csv("/content/Data_set.csv")
data.info()
```
![image](https://github.com/user-attachments/assets/bac923f5-4738-48ab-b8f9-06afe0c23f3b)
```
import pandas as pd
data = pd.read_csv("/content/Data_set.csv")
data.describe()
```
![image](https://github.com/user-attachments/assets/7fd2be28-eb9d-4319-b450-dba357a89736)
```
import pandas as pd
data = pd.read_csv("/content/Data_set.csv")
data.isnull().sum()
```
![image](https://github.com/user-attachments/assets/9d66434e-9be2-4d53-bcb6-aff7d786a34b)
```
import pandas as pd
data = pd.read_csv("/content/Data_set.csv")
data.notnull().sum()
```
![image](https://github.com/user-attachments/assets/3c49ee2e-2f27-492d-bcdf-986786dc12b0)
```
import pandas as pd
data = pd.read_csv("/content/Data_set.csv")
data.fillna(method = 'ffill')
```
![image](https://github.com/user-attachments/assets/9328830b-79cf-488e-95da-c87c08f991dc)
```
import pandas as pd
import seaborn as sns
ir=pd.read_csv('iris.csv')
ir
```
![image](https://github.com/user-attachments/assets/e531f258-894a-49c5-a7e4-a68d25fe30e3)
```
sns.boxplot(x='sepal_width',data=data)
```
![image](https://github.com/user-attachments/assets/7cae3f4b-c5eb-46ae-a855-8e42ed86975e)
```
 c1=data.sepal_width.quantile(0.25)
 c3=data.sepal_width.quantile(0.75)
 iq=c3-c1
 print(c3)
```
![image](https://github.com/user-attachments/assets/c5e41def-7d63-48e9-a964-b87b111c64b3)
```
rid=data[((data.sepal_width<(c1-1.5*iq))|(data.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/eee25860-c416-4874-82c9-da5cd40658b4)
```
delid=data[~((data.sepal_width<(c1-1.5*iq))|(data.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/28b9afa6-9947-48b3-af52-60533c5e32dc)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/81c7a258-b155-4720-91c6-ec2ed6754719)
```
import scipy.stats as stats
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
data = pd.read_csv("/content/heights.csv")
data
```
![image](https://github.com/user-attachments/assets/bc744b2a-3cb5-4cc8-bae9-1831433c8e27)
```
z = np.abs(stats.zscore(data['height']))
z
```
![image](https://github.com/user-attachments/assets/b84b8c17-60cb-4ed4-9f0f-e4b29913f8f4)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
df
```
![image](https://github.com/user-attachments/assets/ef01703f-3703-4826-bd63-b74f4c47549b)
```
iqr = q3 -q1
iqr
```
![image](https://github.com/user-attachments/assets/d093f8ac-0624-4547-9665-e5fd26c199e3)


```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/d857d9d0-26cb-41be-889a-9442816900d4)


```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/3d488194-9092-4b8e-8030-695ebd25dc8a)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/e073f429-2aba-4113-8a7b-10c19c2ae488)







# Result
         Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method

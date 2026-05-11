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
data=pd.read_csv("sampleids.csv")
data
```
<img width="903" height="728" alt="Screenshot 2026-05-11 103058" src="https://github.com/user-attachments/assets/adaf986f-33ef-4532-8c64-ab96a5622d23" />

```
data.info()
```
<img width="497" height="417" alt="Screenshot 2026-05-11 102850" src="https://github.com/user-attachments/assets/d315b00a-8a4d-4b0d-9d4d-72bf68d7bb87" />

```
data.head()
```
<img width="876" height="213" alt="image" src="https://github.com/user-attachments/assets/2e83051c-27f5-4562-b38b-1275e0e3184b" />

```
data.tail()
```
<img width="898" height="218" alt="image" src="https://github.com/user-attachments/assets/7092a15d-dfd0-413b-95e7-a570df085001" />

```
data.describe()
```
<img width="797" height="300" alt="Screenshot 2026-05-11 103046" src="https://github.com/user-attachments/assets/9f675f38-08c0-46a7-a30c-f79ef8bb894e" />

```
data.isnull()
```
<img width="797" height="722" alt="Screenshot 2026-05-11 103116" src="https://github.com/user-attachments/assets/50391a8d-02d2-4357-bdee-2e7ff56efd0b" />

```
data.isnull().sum()
```
<img width="166" height="292" alt="Screenshot 2026-05-11 103131" src="https://github.com/user-attachments/assets/5e61cf93-181a-46f7-8fef-3d74e9b82bfe" />

```
data.dropna()
```
<img width="925" height="472" alt="Screenshot 2026-05-11 103157" src="https://github.com/user-attachments/assets/21c4e533-7367-48d5-92b1-3d2589b14c93" />

```
data1.fillna(method='ffill')
```
<img width="896" height="725" alt="image" src="https://github.com/user-attachments/assets/c2feda03-4422-41f8-a740-7c27e1c6b018" />

```
df.fillna(method='bfill')
```
<img width="912" height="720" alt="image" src="https://github.com/user-attachments/assets/583f677b-bf5c-4e3f-9b7f-ff7de42c04b6" />

```
df.fillna({'NAME':'RIYA','GENDER':'FEMALE','ADDRESS':'CHENNAI','M1':90,'M2':90,'M3':89,'M4':87})
```
<img width="917" height="717" alt="image" src="https://github.com/user-attachments/assets/55bb51a0-d801-4cd6-9962-b3d6b61b68bd" />

```
import numpy as np
from scipy import stats
ir=pd.read_csv("iris.csv")
ir
```
<img width="537" height="443" alt="image" src="https://github.com/user-attachments/assets/53f64d03-3376-4363-80c4-6f0d9be1f960" />

```
ir.describe()
```
<img width="495" height="317" alt="image" src="https://github.com/user-attachments/assets/3d8eba12-4e6e-4ae4-9968-bcfd336b46cb" />

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
<img width="692" height="576" alt="image" src="https://github.com/user-attachments/assets/f6164198-76a4-495a-99bf-b84c60b53542" />

```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```
<img width="48" height="38" alt="image" src="https://github.com/user-attachments/assets/6b17cfde-5f36-4e62-b8a8-122215541ffd" />

```
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```
<img width="335" height="128" alt="image" src="https://github.com/user-attachments/assets/f5437c61-e6a2-450f-8dff-178a2f729902" />

```
delid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
delid
```
<img width="563" height="447" alt="image" src="https://github.com/user-attachments/assets/01d5f296-b981-4cbc-b003-2e1bfd6e7b4e" />

```
sns.boxplot(x='sepal_width',data=delid)
```
<img width="742" height="581" alt="image" src="https://github.com/user-attachments/assets/8a85e001-8954-45a5-b042-492533118a87" />

```
z=np.abs(stats.zscore(ir['sepal_width']))
z
```
<img width="477" height="283" alt="image" src="https://github.com/user-attachments/assets/983a6b98-1d92-4919-8f8d-bc8334fa5614" />

```
ir1=ir[z<3]
ir1
```
<img width="740" height="552" alt="image" src="https://github.com/user-attachments/assets/7a795fc6-50b9-401b-9522-58950ee7fd65" />

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.

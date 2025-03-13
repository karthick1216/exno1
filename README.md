## Exno:1
## Data Cleaning Process

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

# Register no : 212224230114
# date : 13/3/25
~~~
import pandas as pd
lk = pd.read_csv('/content/SAMPLEIDS.csv')
lk
~~~

![Screenshot 2025-03-13 102253](https://github.com/user-attachments/assets/bc15ab00-07c2-4fbe-8454-35401c551803)
~~~
lk.isnull().sum()
~~~
![Screenshot 2025-03-13 102354](https://github.com/user-attachments/assets/96b75406-08e7-4896-abc5-ed20b8fe89ac)
~~~
lk.isnull().any()
~~~
![Screenshot 2025-03-13 102806](https://github.com/user-attachments/assets/235814d5-ed92-484f-bc16-3e6f6f231a55)

~~~
lk.dropna()
~~~
![Screenshot 2025-03-13 102958](https://github.com/user-attachments/assets/094e75a3-ee32-4de8-8873-5e62bb535ab0)
~~~
lk.fillna(0)
~~~
![Screenshot 2025-03-13 103059](https://github.com/user-attachments/assets/5d4b0cee-2db2-4903-839b-d8ff4c2720c0)
~~~
lk.fillna(method = 'ffill')
~~~
![Screenshot 2025-03-13 103136](https://github.com/user-attachments/assets/64aafb59-e3e0-4225-9c09-7e30f43a89af)
~~~
lk.fillna(method='bfill')
~~~
![Screenshot 2025-03-13 103204](https://github.com/user-attachments/assets/ca1096b1-c868-4d09-be43-973fb7d7383e)
~~~
lk.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
~~~
![Screenshot 2025-03-13 103243](https://github.com/user-attachments/assets/cb4be99b-e3d1-492e-992d-72d814d401cf)
~~~
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
ir= pd.read_csv('/content/iris.csv')
ir
~~~
![Screenshot 2025-03-13 103343](https://github.com/user-attachments/assets/c62e5536-690e-4722-8869-b3c3c87a8df6)
~~~
ir.describe()
~~~
![Screenshot 2025-03-13 103423](https://github.com/user-attachments/assets/3c0dd03b-bcf4-4204-9a2d-ab51cdd47ef6)
~~~
sns.boxplot(x = 'sepal_width',data=ir)
~~~
![Screenshot 2025-03-13 103506](https://github.com/user-attachments/assets/cbc7d156-96e4-475b-b49e-70a67e0a451b)

~~~
q1 = ir.sepal_width.quantile(0.25)
q3 = ir.sepal_width.quantile(0.75)
iqr = q3-q1
print(iqr)
~~~
![Screenshot 2025-03-13 103600](https://github.com/user-attachments/assets/02ce3db4-7607-458d-b53c-4d4fda39860a)
~~~
rid=ir[(ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr))]
rid['sepal_width']
~~~
![Screenshot 2025-03-13 103637](https://github.com/user-attachments/assets/746db571-6a13-41e6-a2b1-4d4ccd3031d5)
~~~
delid=ir[~(ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr))]
delid
~~~
![Screenshot 2025-03-13 103713](https://github.com/user-attachments/assets/d9a9f70a-774a-4581-8e33-66ce7afb1970)

~~~
sns.boxplot(x='sepal_width',data=delid)
~~~
![Screenshot 2025-03-13 103753](https://github.com/user-attachments/assets/29277704-c118-44f7-95c9-30bf1081dc4a)
~~~
dataset=pd.read_csv("/content/heights.csv")
dataset
~~~
![Screenshot 2025-03-13 103829](https://github.com/user-attachments/assets/fd8c1d01-5596-45e1-9f7c-0a2c4a74b83b)
~~~
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

lk = pd.read_csv('/content/heights.csv')
q1 = lk.height.quantile(0.25)
q2 = lk.height.quantile(0.50)
q3 = lk.height.quantile(0.75)
iqr = q3-q1
print(iqr)
~~~
![Screenshot 2025-03-13 103908](https://github.com/user-attachments/assets/25d34c3a-5f14-4dd0-b3c9-08c23b7ec5cd)
~~~
low = q1-1.5*iqr
high = q3+1.5*iqr
print(low)
print(high)
~~~
![Screenshot 2025-03-13 103947](https://github.com/user-attachments/assets/b49e722e-edcb-4c37-a259-52a8e0b3df65)
~~~
lk1 = lk[((lk['height']>=low) & (lk['height']<=high))]
lk1
~~~
![Screenshot 2025-03-13 104026](https://github.com/user-attachments/assets/8742c631-8f44-40b1-9e4d-3e89661e9160)
~~~
import scipy.stats as stats
z = np.abs(stats.zscore(lk['height']))
print(z)
~~~
![Screenshot 2025-03-13 104103](https://github.com/user-attachments/assets/84733fda-f6a2-445a-a9fe-90c8e731279c)
~~~
lk1 = lk[z<3]
lk1
~~~

![Screenshot 2025-03-13 104136](https://github.com/user-attachments/assets/bed4ea23-644d-4108-bbc5-a2de88a43d8b)

# Result
            Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.

#EX.NO:1
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

# Coding and Output:

NAME: SRIRAM.S
REG NO:212225240155

```
import pandas as pd
data=pd.read_csv("sampleids.csv")
data
```
<img width="825" height="638" alt="{16A18D67-41DE-49A9-B1EB-9128E52AEF76}" src="https://github.com/user-attachments/assets/74efa86f-a2f8-4e59-80df-bd7cb876f4bb" />

```
data.info()
```

<img width="383" height="366" alt="{1E633CA1-5D9D-41F8-B1B7-9C73545C0A38}" src="https://github.com/user-attachments/assets/72c6c919-08cd-42c3-b754-2317e12d0e69" />

```
print(data.head())
print(data.tail())
```

<img width="700" height="503" alt="{157BE35F-5FFA-4E80-9E54-3E7E732F062D}" src="https://github.com/user-attachments/assets/0b350725-2bc6-40d0-93fb-4d89d28b7631" />

```
data.isnull()
```

<img width="719" height="639" alt="{7D1352D4-CBE0-426E-8728-3F8CAFAACAEE}" src="https://github.com/user-attachments/assets/89d3299d-6574-4097-ac6b-2c9d3ed32388" />

```
data.isnull().sum()
```

<img width="127" height="263" alt="{2A10112B-B89F-4156-9AF5-0B4CCFD6C6B3}" src="https://github.com/user-attachments/assets/17a4e638-4ade-4f7c-8c06-3fb20a0cffd6" />

```
data.dropna()
```
<img width="813" height="425" alt="{36C76773-C00E-4484-BCC3-EE284FD08E89}" src="https://github.com/user-attachments/assets/d733e516-edbe-46c5-a51f-12f0a2e5be10" />

```
data.fillna(method='ffill')
```

<img width="831" height="648" alt="{793D6B5C-B933-44ED-AF85-F1B2B0EE578F}" src="https://github.com/user-attachments/assets/e7a678aa-99b7-4df5-b809-c36e68d93fb7" />


```
data.fillna(method='bfill')
```

<img width="822" height="645" alt="{8DB6E13E-F05D-43CA-86BA-86A14C2DE5E3}" src="https://github.com/user-attachments/assets/6407690b-fd48-4482-8619-d0d48c8ed379" />

```
data.fillna({'NAME':'RIYA','GENDER':'FEMALE','ADDRESS':'CHENNAI','M1':90,'M2':90,'M3':89,'M4':87})
```

<img width="815" height="645" alt="{1331220D-7EE6-47E3-82E6-8A29CAFA61F2}" src="https://github.com/user-attachments/assets/875a2fc3-e68c-4899-b554-d6b77aa18ce0" />

```
import numpy as np
from scipy import stats
ir=pd.read_csv("iris.csv")
ir
```


<img width="514" height="395" alt="{B5C0E4E4-9873-4080-8A39-0C6FFFE64963}" src="https://github.com/user-attachments/assets/db6f0cb1-7658-464a-86bf-8a851ffb9670" />

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```

<img width="596" height="521" alt="{2202E8AB-34DD-43BA-BE2F-9B688DAF8FEB}" src="https://github.com/user-attachments/assets/436985e2-719a-4a41-ad64-48f2f0144b4c" />

```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
print()
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
print(rid['sepal_width'])
```

<img width="450" height="151" alt="{79C85794-6EB8-4AEC-BDB6-9916F33559B9}" src="https://github.com/user-attachments/assets/ea4d8257-d1d1-43a5-93d7-1d1a31a3c787" />

```
delid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
delid
```

<img width="489" height="400" alt="{7111EFD8-868F-4FEF-A4E4-DD626BFE3EF5}" src="https://github.com/user-attachments/assets/67e8b615-2f5e-436d-879f-4f16696721bc" />

```
sns.boxplot(x='sepal_width',data=delid)
```

<img width="612" height="532" alt="{32AEA4C1-DF94-4E28-9012-C26F825E91B3}" src="https://github.com/user-attachments/assets/414f3faa-0fbf-49cd-80f5-b00ba2768906" />

```
z=np.abs(stats.zscore(ir['sepal_width']))
z
```

<img width="432" height="243" alt="{F935B029-7657-4B71-A9DA-64AB30CF4F46}" src="https://github.com/user-attachments/assets/36f1a779-31d8-4974-b30a-c68092997854" />


```
ir1=ir[z<3]
ir1
```

<img width="486" height="399" alt="{F8C414BC-A32C-4BFC-A073-96DCBEB23F9F}" src="https://github.com/user-attachments/assets/54524c87-3455-4731-9aa9-ea90888ca025" />

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.

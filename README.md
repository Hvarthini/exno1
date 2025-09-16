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
import pandas as pd df=pd.read_csv("/content/iris.csv") df
<img width="810" height="630" alt="image" src="https://github.com/user-attachments/assets/9604647f-eda1-47c8-a235-1761f27829e5" />
df.head()
<img width="755" height="313" alt="image" src="https://github.com/user-attachments/assets/41488d3a-ce1e-4cf2-a64e-691dbaf270d5" />
df.tail()
<img width="811" height="323" alt="image" src="https://github.com/user-attachments/assets/dba8d9e4-7cd5-4ce2-95f2-3fb644a8dd0a" />
df.isnull()
<img width="753" height="588" alt="image" src="https://github.com/user-attachments/assets/a22e462e-e58c-450f-9191-4436f41d2fcb" />
df.dropna(axis=0)
<img width="819" height="573" alt="image" src="https://github.com/user-attachments/assets/364d3e3a-b74d-4df5-8199-dfef0d0e2098" />
df.dropna(axis=1)
<img width="794" height="597" alt="image" src="https://github.com/user-attachments/assets/8d39eccb-ed37-4346-846c-bb03d3dfa8a5" />
df.fillna(0)
<img width="787" height="581" alt="image" src="https://github.com/user-attachments/assets/3759bccf-c155-4884-bb17-ddf435aca0e3" />
df_dropped=df.dropna() df_dropped
<img width="804" height="599" alt="image" src="https://github.com/user-attachments/assets/4347ee21-5d17-4700-9208-bd0e825e1a46" />
import seaborn as sns suren=pd.read_csv('/content/iris.csv') df
<img width="757" height="440" alt="image" src="https://github.com/user-attachments/assets/fd9d8ba0-e3cc-4f9a-a80d-90a16404ee44" />
df.describe()
<img width="773" height="641" alt="image" src="https://github.com/user-attachments/assets/3d990b8f-fc91-4089-a1bd-b449d5a9d7c4" />
sns.boxplot(x='sepal_width',data=df)
<img width="748" height="635" alt="image" src="https://github.com/user-attachments/assets/5892e6b6-4c77-4cb2-9e4a-b1148b8ddc8e" />
q1=df.sepal_width.quantile(0.25) q3=df.sepal_width.quantile(0.75) iqr=q3-q1 print(iqr)
rid=df[((df.sepal_width<(q1-1.5iqr))|(df.sepal_width>(q3+1.5iqr)))] rid['sepal_width']
<img width="761" height="522" alt="image" src="https://github.com/user-attachments/assets/a2d8cf7a-22c9-4f2a-9244-e096c5d1e255" />
delid=df[~((df.sepal_width<(q1-1.5iqr))|(df.sepal_width>(q3+1.5iqr)))] delid
<img width="756" height="604" alt="image" src="https://github.com/user-attachments/assets/ed454f9a-2b7e-4a70-b94d-e79fa5c09fa9" />
sns.boxplot(x='sepal_width',data=delid)
<img width="741" height="653" alt="image" src="https://github.com/user-attachments/assets/a2dde136-9ead-4385-8554-2d756b12ffbe" />
import matplotlib.pyplot as plt import pandas as pd import numpy as np import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv") dataset
<img width="474" height="783" alt="image" src="https://github.com/user-attachments/assets/a244098b-352a-4b59-af55-0d0f3abf6167" />
df=pd.read_csv("/content/heights.csv") q1=df['height'].quantile(0.25) q2=df['height'].quantile(0.5) q3=df['height'].quantile(0.75)

iqr=q3-q1 iqr

low=q1-1.5*iqr low

high=q3+1.5*iqr high
<img width="487" height="564" alt="image" src="https://github.com/user-attachments/assets/9bbf76b9-9463-4ab0-837e-abf9da0fba98" />
z=np.abs(stats.zscore(suren['sepal_length'])) z
<img width="799" height="748" alt="image" src="https://github.com/user-attachments/assets/1edbfa8e-a4e1-49b6-9d9c-9ac0f5b67a8e" />
suren1=suren[z<3] suren1
<img width="782" height="600" alt="image" src="https://github.com/user-attachments/assets/8d04f882-0182-46aa-9fbb-9841d79f074f" />

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.

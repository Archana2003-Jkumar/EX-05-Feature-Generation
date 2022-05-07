# EX-05-Feature-Generation


## AIM
To read the given data and perform Feature Generation process and save the data to a file. 

# Explanation
Feature Generation (also known as feature construction, feature extraction or feature engineering) is the process of transforming features into new features that better relate to the target.
 

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature Generation techniques to all the feature of the data set
### STEP 4
Save the data to the file


# CODE
## Encoding Data .csv
```
import pandas as pd
df=pd.read_csv("Encoding Data.csv")
df

from sklearn.preprocessing  import LabelEncoder , OrdinalEncoder
from sklearn.preprocessing import StandardScaler as sc
from category_encoders import BinaryEncoder
be=BinaryEncoder()
data1=be.fit_transform(df["bin_1"])
data1

df2=df.copy()
be1=BinaryEncoder()
data2=be1.fit_transform(df2["bin_2"])
df2["bin_2"]=be1.fit_transform(df2[["bin_2"]])
df2

df3=df2.copy()
oe=OrdinalEncoder()
oe.fit_transform(df3[["ord_2"]])

df3
le=LabelEncoder()
df4=df3.copy()
le.fit_transform(df4[["nom_0"]])
df4["nom_0"]=le.fit_transform(df4[["nom_0"]])
df4

from category_encoders import BinaryEncoder
be=BinaryEncoder()
be.fit_transform(df4[["bin_1"]])
df4

from sklearn.preprocessing import StandardScaler
ss=StandardScaler()
df5=pd.DataFrame(ss.fit_transform(df4),columns=['id','bin_1','bin_2','nom_0','ord_2'])
df5
```
## Data.csv 
```
import pandas as pd
df=pd.read_csv("data.csv")
df

df1=df.copy()
be=BinaryEncoder()
be.fit_transform(df1[["bin_1"]])
df1["bin_1"]=be.fit_transform(df1[["bin_1"]])
df1

df2=df1.copy()
be2=BinaryEncoder()
be2.fit_transform(df2[["bin_2"]])
df2["bin_2"]=be2.fit_transform(df2[["bin_2"]])
df2

df3=df2.copy()
le=LabelEncoder()
le.fit_transform(df3[["City"]])
df3["City"]=le.fit_transform(df3[["City"]])
oe=OrdinalEncoder()

df4=df3.copy()
df4["Ord_1"]=oe.fit_transform(df4[["Ord_1"]])
df4

df5=df4.copy()
df5["Ord_2"]=oe.fit_transform(df5[["Ord_2"]])
df5

from sklearn.preprocessing import StandardScaler
ss=StandardScaler()
df6=pd.DataFrame(ss.fit_transform(df5),columns=['id','bin_1','bin_2','City','Ord_1','Ord_2','Target'])
df6

from sklearn.preprocessing import MinMaxScaler
scaler=MinMaxScaler()
df7=pd.DataFrame(scaler.fit_transform(df6),columns=['id','bin_1','bin_2','City','Ord_1','Ord_2','Target'])
df7

from sklearn.preprocessing import MaxAbsScaler
maxabsscaler=MaxAbsScaler()
df8=pd.DataFrame(maxabsscaler.fit_transform(df7),columns=['id','bin_1','bin_2','City','Ord_1','Ord_2','Target'])
df8

from sklearn.preprocessing import RobustScaler
rscaler = RobustScaler()
df9=pd.DataFrame(rscaler.fit_transform(df8),columns=['id','bin_1','bin_2','City','Ord_1','Ord_2','Target'])
df9
```
## Titanic Data set
```
import pandas as pd
df=pd.read_csv("titanic_dataset.csv")
df

del df["Name"]
del df["Cabin"]
del df["Ticket"]
df

df1=df.copy()
from sklearn.preprocessing  import LabelEncoder , OrdinalEncoder
from sklearn.preprocessing import StandardScaler as sc
from category_encoders import BinaryEncoder
be=BinaryEncoder()
df["Age"]=df["Age"].fillna(df["Age"].median())
df

df["Embarked"]=df["Embarked"].fillna(df["Embarked"].mode()[0])
df

oe=OrdinalEncoder ()
oe.fit_transform(df[["Embarked"]])

embark=['S','C','Q']
emb=OrdinalEncoder(categories=[embark])
emb

emb.fit_transform(df[['Embarked']])
df["Embarked"]=emb.fit_transform(df[["Embarked"]])
df

be=BinaryEncoder()
newdata=be.fit_transform(df1["Sex"])
newdata

from sklearn.preprocessing import MinMaxScaler
scaler=MinMaxScaler()
df2=pd.DataFrame(scaler.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df2

from sklearn.preprocessing import StandardScaler
ss=StandardScaler()
df3=pd.DataFrame(ss.fit_transform(df2),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df3

from sklearn.preprocessing import MaxAbsScaler
maxabsscaler=MaxAbsScaler()
df4=pd.DataFrame(maxabsscaler.fit_transform(df3),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df4

from sklearn.preprocessing import RobustScaler
rscaler = RobustScaler()
df5=pd.DataFrame(rscaler.fit_transform(df4),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df5
```
# OUPUT
![Screenshot(218).png](./Screenshot%20(218).png)
![Screenshot(219).png](./Screenshot%20(219).png)
![Screenshot(220).png](./Screenshot%20(220).png)
![Screenshot(221).png](./Screenshot%20(221).png)
![Screenshot(222).png](./Screenshot%20(222).png)
![Screenshot(224).png](./Screenshot%20(224).png)

## Data.csv
![Screenshot(236).png](./Screenshot%20(236).png)
![Screenshot(237).png](./Screenshot%20(237).png)
![Screenshot(238).png](./Screenshot%20(238).png)
![Screenshot(239).png](./Screenshot%20(239).png)
![Screenshot(240).png](./Screenshot%20(240).png)
![Screenshot(241).png](./Screenshot%20(241).png)
![Screenshot(242).png](./Screenshot%20(242).png)
![Screenshot(243).png](./Screenshot%20(243).png)
# Titanic.csv
![Screenshot(251).png](./Screenshot%20(251).png)
![Screenshot(252).png](./Screenshot%20(252).png)
![Screenshot(253).png](./Screenshot%20(253).png)
![Screenshot(254).png](./Screenshot%20(254).png)
![Screenshot(255).png](./Screenshot%20(255).png)
![Screenshot(256).png](./Screenshot%20(256).png)
![Screenshot(257).png](./Screenshot%20(257).png)
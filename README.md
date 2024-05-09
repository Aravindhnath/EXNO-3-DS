# EXNO-3-DS Feature Encoding and Transformation

## AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

## ALGORITHM:

STEP 1:Read the given Data.

STEP 2:Clean the Data Set using Data Cleaning Process.

STEP 3:Apply Feature Encoding for the feature in the data set.

STEP 4:Apply Feature Transformation for the feature in the data set.

STEP 5:Save the data to the file.


## FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

## Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

## CODING AND OUTPUT:

```
NAME: ARAVINDHNATH TR
REGNO: 212222100005
```

~~~
     import pandas as pd
     df=pd.read_csv("/content/Encoding Data.csv")
     df
~~~

  ![Output](Op1-ds3.png)


  ~~~
    from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
    pm=['Hot','Warm','Cold']
    e1=OrdinalEncoder(categories=[pm])
    e1.fit_transform(df[["ord_2"]])
~~~

  ![Output](Op2-ds3.png)


~~~
    df['bo2']=e1.fit_transform(df[["ord_2"]])
    df
~~~

  ![Output](Op3-ds3.png)

~~~
    df['bo2']=e1.fit_transform(df[["ord_2"]])
    df
~~~
  ![Output](Op4-ds3.png)

~~~
    le=LabelEncoder()
    dfc=df.copy()
    dfc['ord_2']=le.fit_transform(dfc['ord_2'])
    dfc
~~~

  ![Output](Op5-ds3.png)

  ~~~
    from sklearn.preprocessing import OneHotEncoder
    ohe=OneHotEncoder(sparse=False)
    df2=df.copy()
    enc=pd.DataFrame(ohe.fit_transform(df2[['nom_0']]))
    df2=pd.concat([df2,enc],axis=1)
    df2
~~~

  ![Output](Op6-ds3.png)

  ~~~
    pd.get_dummies(df2,columns=["nom_0"])
~~~

  ![Output](Op7-ds3.png)

  ~~~
    pip install --upgrade category_encoders
  ~~~

  ![Output](Op8-ds3.png)

~~~
    from category_encoders import BinaryEncoder
    df=pd.read_csv("/content/data.csv")
    be=BinaryEncoder()
    nd=be.fit_transform(df['Ord_2'])
    fb=pd.concat([df,nd],axis=1)
    dfb1=df.copy()
    dfb
 
 ~~~

  ![Output](Op9-ds3.png)

 ~~~
    from category_encoders import TargetEncoder
    te=TargetEncoder()
    cc=df.copy()
    new=te.fit_transform(X=cc["City"],y=cc["Target"])
    cc=pd.concat([cc,new],axis=1)
    cc
~~~

  ![Output](Op10-ds3.png)

~~~
    import pandas as pd
    from scipy import stats
    import numpy as np
    df=pd.read_csv("/content/Data_to_Transform.csv")
    df
~~~

  ![Output](Op11-ds3.png)

~~~
    df.skew()
~~~

  ![Output](Op12-ds3.png)

~~~
    np.log(df["Highly Positive Skew"])
~~~

  ![Output](Op13-ds3.png)

~~~
    np.reciprocal(df["Moderate Positive Skew"])
~~~

  ![Output](Op14-ds3.png)

~~~
    np.sqrt(df["Highly Positive Skew"])
~~~

  ![Output](Op15-ds3.png)

~~~
    np.square(df["Highly Positive Skew"])
~~~

  ![Output](Op16-ds3.png)

~~~
   df["Highly Positive Skew_boxcox"],parameters=stats.boxcox(df["Highly Positive Skew"])
   df
~~~

  ![Output](Op17-ds3.png)

~~~
    df["Moderate Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Moderate Negative Skew"])
    df.skew()
~~~

  ![Output](Op18-ds3.png)

~~~
    df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
    df.skew()

~~~
  ![Output](Op19-ds3.png)

~~~
   import matplotlib.pyplot as plt
   import seaborn as sns
   import statsmodels.api as sm
   import scipy.stats as stats

   sm.qqplot(df["Moderate Negative Skew"],line='45')

   plt.show()
  ~~~

  ![Output](Op20-ds3.png)

~~~
    sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
~~~

  ![Output](Op21-ds3.png)

~~~
    from sklearn.preprocessing import QuantileTransformer
    qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)

    df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])

    sm.qqplot(df["Moderate Negative Skew"],line='45')
    plt.show()
    
~~~

  ![Output](Op22-ds3.png)


  ## RESULT:
  
  Hence performing Feature Encoding and Transformation process is Successful.

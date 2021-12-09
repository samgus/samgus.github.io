## NYC Park Maintenance

### What is the project about?

We want to test how often NYC parks receives maintenance depending on where they are built, what borough they are in, and that show when the park was built, what borough it is in, and when the last time they received maintenance.

### What is this significant?

Parks are so valuable and enrich the lives of so many New Yorkers. There’s nothing like being in a beautiful park that is very well taken care of. It is important to solve this problem because there are parks in New York that are not properly taken care of and they are so important to our mental health to be in a nice, peaceful, and clean environment. From kids to adults, everyone needs nice quality parks accessible to them, no matter where in New York City they live.

### Links:
[Open NYC Data for Park Maintainance (2020)](https://www.nycgovparks.org/news/archive)

### Import Libraries:
```markdown
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
import seaborn as sns
import geoplotlib as geoplot
```
### User Inputs:
```markdown
#Get input and output file names:
df1 = pd.read_csv('parksProperties.csv')
df2 = pd.read_csv('nycParkFunding2020.csv')
df3 = pd.read_csv('parkZones.csv')
outFile = input('Enter output file name: ')
```
### Making a Function convertMoney():
```markdown
#We want to get to the sum of quarterly funding for NYC parks, so we have to converts the strings into floats.
def convertMoney(col):
    df[col] = df[col].apply(lambda x: x.replace('$','')) #striping dollar sign
    df[col] = df[col].apply(lambda x: x.replace(',','')) #striping comma
    df[col] = df[col].astype(float) #converting to float
    return df
```
### Organizing the data:
```markdown
#For the 1st Dataframe
df1 = df1[['ACQUISITIONDATE','LOCATION','Sign Name','multipolygon']].dropna()
df1['ACQUISITIONDATE'] = df1['ACQUISITIONDATE'].apply(lambda x: x.replace(' 00:00:00.0000000','')) #striping the string of zeros
df1 = df1[df1["Sign Name"] != 'Park']
```
```markdown
#For the 2nd Dataframe
df2 = df2[['Sign Name','Borough Code','Sector Desc.','Q1WorkOrderCost',
'Q2WorkOrderCost','Q3WorkOrderCost','Q4WorkOrderCost']].dropna()
df2 = df2[df2["Sign Name"] != 'Park']
df2 = convertMoney('Q1WorkOrderCost')
df2 = convertMoney('Q2WorkOrderCost')
df2 = convertMoney('Q3WorkOrderCost')
df2 = convertMoney('Q4WorkOrderCost')
df2['Total Spending'] = (df2['Q1WorkOrderCost'] + df2['Q2WorkOrderCost']
 + df2['Q3WorkOrderCost'] + df2['Q4WorkOrderCost'])
```
```markdown
#Combining them into one dataframe to analyze
df = pd.merge(df1, df2)
df.to_csv(outFile)
```
Now, we are organzing the data from the orginal csv that we pulled to use for our purposes. Notice that now we have a column 'Total Spending' so we can easily see which parks are recieving adequate funding for maintainence.

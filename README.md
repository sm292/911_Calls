# 911_Calls
# 911 Calls Data Collected from Kaggle is orgamized and visualization is done 
## Importing Libraries

import pandas as pd
import numpy as np

import matplotlib.pyplot as plt

## Reading CSV

df = pd.read_csv('911.csv')

## Checking Data Info

df.info()

## DataFrame Check

df.head()

## TOP 5 ZIP Codes

df['zip'].value_counts().head(5)

## TOP 5 Township

df['twp'].value_counts().head(5)

## unique title count

df['title'].nunique()

## Creating new features

**Creating a new column 'Reason', if the title column value is EMS: BACK PAINS/INJURY , the Reason column value would be EMS.**

df['Reason'] = df['title'].apply(lambda x: x.split(':')[0])

df.head()

**__Most Common Reason__**

df['Reason'].nunique()

df['Reason'].value_counts()

**__Most common Reason Plotting__**

import seaborn as sns

sns.countplot(x = 'Reason',data=df,palette='crest')

sns.countplot(x = 'Reason',data=df,palette='mako')

sns.countplot(x = 'Reason',data=df,palette='coolwarm')

type(df['timeStamp'].iloc[0])

df['timeStamp'].iloc[0]

**__Dividing TimeStrap into Date Time and making columns Hour Month and Day of Week__**

df['timeStamp'] = pd.to_datetime(df['timeStamp'])

df['Hour'] = df['timeStamp'].apply(lambda time: time.hour)
df['Month'] = df['timeStamp'].apply(lambda time: time.month)
df['Day of Week'] = df['timeStamp'].apply(lambda time: time.dayofweek)

df.head()

**__Mapping Day of the Week From Number to a Specific Day__**

dmap = {0:'Mon',1:'Tue',2:'Wed',3:'Thu',4:'Fri',5:'Sat',6:'Sun'}

df['Day of Week'] = df['Day of Week'].map(dmap)

df.info()

**countplot of the Day of Week column wrt Reason column**

sns.countplot(x='Day of Week', data=df, hue='Reason')
plt.legend(bbox_to_anchor=(1.05, 1), loc=2, borderaxespad=0.)

**Now same for Month**

sns.countplot(x='Month', data=df, hue='Reason')
plt.legend(bbox_to_anchor=(1.05, 1), loc=2, borderaxespad=0.)

__NOTE:  Saw misssing values and hence grouping by month__

byMonth = df.groupby(by='Month').count()

byMonth

__Lineplot of the title wrt month__

byMonth['title'].plot()

**__Targettting the missing values wrt the linear model plot__**

sns.lmplot(x='Month',y='twp',data=byMonth.reset_index())

## **Creating date column** 

df['Date'] = df['timeStamp'].apply(lambda x: x.date())

df.info()

## Counting the Calls as per date values

df['Date'] = pd.to_datetime(df['Date'])

df.groupby('Date').count()['twp'].plot()
plt.tight_layout()

## Creating date wise plot WRT Reason of the Calls

df[df['Reason']=='Traffic'].groupby('Date').count()['twp'].plot()
plt.title('Traffic')
plt.tight_layout()

df[df['Reason']=='EMS'].groupby('Date').count()['twp'].plot()
plt.title('EMS')
plt.tight_layout()

df[df['Reason']=='Fire'].groupby('Date').count()['twp'].plot()
plt.title('Fire')
plt.tight_layout()

## Unstacking the day of week and hour 

byDOW = df.groupby(by=['Day of Week', 'Hour']).count()['Reason'].unstack()
byDOW

## Heatmap of the unstacked data

plt.figure(figsize=(12,8))
sns.heatmap(byDOW,cmap='viridis')

## Clustermap of the unstacked data

sns.clustermap(byDOW,cmap='viridis')

## Unstacking by Month

monthAScolumn = df.groupby(['Day of Week','Month']).count()['Reason'].unstack()
monthAScolumn

plt.figure(figsize=(12,6))
sns.heatmap(monthAScolumn,cmap='coolwarm')

plt.figure(figsize=(12,6))
sns.clustermap(monthAScolumn,cmap='coolwarm')

## Continued






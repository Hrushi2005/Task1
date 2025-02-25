import pandas as pd
from sklearn.impute import SimpleImputer
data=pd.read_csv('Data.csv')
imputer_mode = SimpleImputer(strategy='most_frequent')#it is used to add most frequently data
print(data.isna().sum())#finding no.of none values
print('')
data['Age']=imputer_mode.fit_transform(data[['Age']])
print('filling  Age column none value with mean value by using scikit learn library')
print('')
print(data.isna().sum())#showingnone values
print('')
data['Salary']=data['Salary'].fillna(data['Salary'].median(),inplace=False)
print('filling  Salary and Department columns none value with median value by using pandas library')
data["Department"]=data["Department"].fillna(data['Department'].mode()[0],inplace=False)
data.to_excel("Final_data.xlsx")

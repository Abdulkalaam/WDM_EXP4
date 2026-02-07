### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
## DATE: 07-02-2026
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program 1:
```
import pandas as pd
df=pd.read_csv("C:\\Users\\admin\\Desktop\\SEM3\\WDM\\clustervisitor.csv")
df

cluster={"Young":(df['Age']<=30),"Middle":((df['Age']>30)&(df['Age']<=50)),"Old":(df['Age']>50)}
print(cluster)

count = []
for g, c in cluster.items():
    visitors = df[c]   
    count.append(len(visitors))
    print(f"Visitors in {g} Group")
    print(visitors)
    print(count)

import matplotlib.pyplot as plt
plt.figure(figsize=(8, 6))
plt.bar(cluster.keys(), count, color='skyblue')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.show()
```
### Output:
<img width="964" height="674" alt="Screenshot 2026-02-07 144702" src="https://github.com/user-attachments/assets/edfb5d5b-0d13-48af-85ba-576313adafd1" />

<img width="884" height="682" alt="Screenshot 2026-02-07 144000" src="https://github.com/user-attachments/assets/a959cc40-44b7-43b0-ad5d-e4208644ff72" />


### Program 2:
```
df=pd.read_csv(r"C:\Users\admin\Desktop\SEM3\WDM\clustervisitor (Salary).csv")

df1=df['Age']
df2=df['Salary']
df3=pd.concat([df1,df2],axis=1)

df3

from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans

sc=StandardScaler()
scaleddata=sc.fit_transform(df3)
print(scaleddata)

kmeans=KMeans(n_clusters=3,random_state=42)
df3['cluster']=kmeans.fit_predict(df3)
df3

plt.scatter(df3['Age'],df3['Salary'],c=df3['cluster'])
plt.xlabel("Age")
plt.ylabel("Income in thousands")
plt.show()
```
### Output:
<img width="1196" height="676" alt="Screenshot 2026-02-07 144128" src="https://github.com/user-attachments/assets/fd2456f2-5d74-4d85-97ba-30c80e01d3ba" />

<img width="1022" height="574" alt="Screenshot 2026-02-07 144512" src="https://github.com/user-attachments/assets/979cea6f-7aaa-4c55-8ee5-aed30148e4c8" />


### Result:
Cluster and Visitor Segmentation for Navigation patterns in Python has been successfully implemented.

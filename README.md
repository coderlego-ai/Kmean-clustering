# Kmean-clustering
#Aditya Sharma
# CASE STUDY 1
# < Case Study 1>
# In a given dataset (attached in the folder), we have information about Wines clustering data.
# Source: https://www.kaggle.com/code/xvivancos/tutorial-clustering-wines-with-k-means/input
# Question 1 Implement the K-mean clustering algorithm for 50 iterations and store the data 
# of each cluster in a respective folder. For example: there will be two folders 
# after the execution of this program and each folder will consist of five CSV 
# files (cluster 1, cluster 2, cluster 3, cluster 4, and cluster 5). These three CSV 
# files will store the cluster data of the respective iteration.
import pandas as pd
import random as r
import math as m


df1 = pd.read_csv(r'C:\Users\91730\Documents\Thapar\2 Year\4th Semester\AI\Lab\EvalDay\EvalDay\Wine.csv')
# df1.drop('', inplace=True, axis=1) 
# print(df1.shape) FOR Dimensions of CSV file
c1 = r.randint(0, 178)
c2 = r.randint(0, 178)
c3 = r.randint(0, 178)
c4 = r.randint(0, 178)
c5 = r.randint(0, 178)
centroid1 = df1.iloc[c1]
centroid2 = df1.iloc[c2]
centroid3 = df1.iloc[c3]
centroid4 = df1.iloc[c4]
centroid5 = df1.iloc[c5]

for i in range(0, 50):
   

    cluster1 = []
    cluster2 = []
    cluster3 = []
    cluster4 = []
    cluster5 = []
    
    
    
    for j in range(0, 177):
        if j == c1 or j == c2 or j == c3 or j==c4 or j==c5:
            continue
        
        point = df1.iloc[j]
        temp1=0
        temp2=0
        temp3=0
        temp4=0
        temp5=0

        for i in range(0,14):
           temp1=temp1+(point.iloc[i]-centroid1.iloc[i])**2
           temp2=temp2+(point.iloc[i]-centroid2.iloc[i])**2
           temp3=temp3+(point.iloc[i]-centroid3.iloc[i])**2
           temp4=temp4+(point.iloc[i]-centroid4.iloc[i])**2
           temp5=temp5+(point.iloc[i]-centroid5.iloc[i])**2
        temp1=m.sqrt(temp1)
        temp2=m.sqrt(temp2)
        temp3=m.sqrt(temp3)
        temp4=m.sqrt(temp4)
        temp5=m.sqrt(temp5)
        if temp1 <= temp2 and temp1 <= temp3 and temp1 <= temp4 and temp1 <= temp5:
            cluster1.append(j)
        elif temp2 <= temp1 and temp2 <= temp3 and temp2 <= temp4 and temp2 <= temp5:
            cluster2.append(j)
        elif temp3 <= temp1 and temp3 <= temp2 and temp3 <= temp4 and temp3 <= temp5:
            cluster3.append(j)
        elif temp4 <= temp1 and temp4 <= temp2 and temp4 <= temp3 and temp4 <= temp5:
            cluster4.append(j) 
        else:
            cluster5.append(j)

    new_centroid1 = df1.iloc[cluster1].mean()
    new_centroid2 = df1.iloc[cluster2].mean()
    new_centroid3 = df1.iloc[cluster3].mean()
    new_centroid4 = df1.iloc[cluster4].mean()
    new_centroid5 = df1.iloc[cluster5].mean()
   
   
    
    print('sizes of cluster 1 2 3 4 and 5 are respectively ',len(cluster1),len(cluster2),len(cluster3),len(cluster4),len(cluster5))
    if (centroid1.equals(new_centroid1) and centroid2.equals(new_centroid2) and centroid3.equals(new_centroid3) and centroid4.equals(new_centroid4) and centroid5.equals(new_centroid5)):
        print(f'Converged at {i}th iteration')
        break
        

    centroid1, centroid2, centroid3, centroid4, centroid5= new_centroid1, new_centroid2, new_centroid3, new_centroid4, new_centroid5        

    cluster1_df = df1.iloc[cluster1]
    cluster2_df = df1.iloc[cluster2]
    cluster3_df = df1.iloc[cluster3]
    cluster4_df = df1.iloc[cluster4]
    cluster5_df = df1.iloc[cluster5]

    cluster1_df.to_csv(r'C:\Users\91730\Documents\Thapar\2 Year\4th Semester\AI\Lab\EvalDay\EvalDay\Folder2\cluster1.csv', index=False)
    cluster2_df.to_csv(r'C:\Users\91730\Documents\Thapar\2 Year\4th Semester\AI\Lab\EvalDay\EvalDay\Folder2\cluster2.csv', index=False)
    cluster3_df.to_csv(r'C:\Users\91730\Documents\Thapar\2 Year\4th Semester\AI\Lab\EvalDay\EvalDay\Folder2\cluster3.csv', index=False)
    cluster4_df.to_csv(r'C:\Users\91730\Documents\Thapar\2 Year\4th Semester\AI\Lab\EvalDay\EvalDay\Folder2\cluster4.csv', index=False)
    cluster5_df.to_csv(r'C:\Users\91730\Documents\Thapar\2 Year\4th Semester\AI\Lab\EvalDay\EvalDay\Folder2\cluster5.csv', index=False)
    
    
    cluster1_df.to_csv(r'C:\Users\91730\Documents\Thapar\2 Year\4th Semester\AI\Lab\EvalDay\EvalDay\Folder3\cluster1.csv', index=False)
    cluster2_df.to_csv(r'C:\Users\91730\Documents\Thapar\2 Year\4th Semester\AI\Lab\EvalDay\EvalDay\Folder3\cluster2.csv', index=False)
    cluster3_df.to_csv(r'C:\Users\91730\Documents\Thapar\2 Year\4th Semester\AI\Lab\EvalDay\EvalDay\Folder3\cluster3.csv', index=False)
    cluster4_df.to_csv(r'C:\Users\91730\Documents\Thapar\2 Year\4th Semester\AI\Lab\EvalDay\EvalDay\Folder3\cluster4.csv', index=False)
    cluster5_df.to_csv(r'C:\Users\91730\Documents\Thapar\2 Year\4th Semester\AI\Lab\EvalDay\EvalDay\Folder3\cluster5.csv', index=False)
    

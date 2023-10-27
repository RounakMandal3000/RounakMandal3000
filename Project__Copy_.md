Task Report

Rounak Mandal October 2023

Introduction

The task which I was given was aimed at finding a learned cost model to predict execution time in ms from the runtime costs of queries. In the context of database management, this information about the relation between the query execution time and its cost can help us in optimizing the execution plans of queries over databases. Understanding the relationship between query execution time and associated costs would often help us refine resource allocation, streamline query process- ing, and enhance overall system performance. Implementing a robust learned cost model would help us by giving decisions for database optimization but also shall ensure the smooth functioning of complex data management systems, leading to improved efficiency and better resource management.

For this task, I was provided with the Baseball dataset on the Postgres (v12) database. In this database, there were 25 tables with each table containing rows and columns and were related with each other. I was also provided with the trained workload which contained the cost units and the execution time.

For the first part of the task, I was asked to use these abstract cost values present in the json file of the workload given along with the execution time of the queries which were present there only, to use as data and then to learn a linear model to estimate their relationship.

For the bonus part, I was asked to extend the idea of using other features to make the model even better such that the model can predict runtime with a much better accuracy than the linear model.

Dataset

The dataset for this task was present in the workload.json file shared. This workload file was a list of dictionaries with each dictionary having two values of each query each being a dictionary, one analyze part and the other as verbose part. Both of them contains information regarding the execution of the query in the database.

The format of the file is as shown below in the following picture:

![](Aspose.Words.935e60f3-abb6-4df7-8ede-7517d6dc9966.001.png)

The data is in the form as mentioned above, and we have a total of around 29000 such dictionary pairs in the workload file.

For the first part of the task, we are interested in the part of Execution time and the cost mentioned in the ”analyze plan” dictionary of the image whose key is a list of lists.

Model

Preprocessing

For the preprocessing part, I followed the following standard steps:

\1) Imported the required libraries required for the task which are these: matplotlib, numpy, json, pandas, seaborn, sklearn and joblib libraries\.

\2)
2

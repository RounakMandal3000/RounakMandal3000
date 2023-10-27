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

![](Aspose.Words.7c780c7e-dac6-4b09-91c6-d981ef049dca.001.png)

The data is in the form as mentioned above, and we have a total of around 29000 such dictionary pairs in the workload file.

For the first part of the task, we are interested in the part of Execution time and the cost mentioned in the ”analyze plan” dictionary of the image whose key is a list of lists.

Model

PART A

For this part, I did these steps:

1) Imported the required libraries required for the task which are these: matplotlib, numpy, json, pandas, seaborn, sklearn and joblib libraries.
1) Took out the data needed from the json file using the following code:

![](Aspose.Words.7c780c7e-dac6-4b09-91c6-d981ef049dca.002.png)

Here, first I read the json file using the json library, then I opened the dictionary under the key of ”query list” where I checked whether its ”analyze plans” and ”Verbose plans” were present or not. In some cases, I notices that both of them were not present and their value was just ”None”. With- out considering this cases, I took out all the cost and the execution time from the data for aroung 29000 data points. Since, there are two costs, I took both of them and only took the execution cost. Hence, after this code, I had three columns

3) Now, following this, I checked the correlation between the two costs and doing so I found that they were completely correlated and hence there was no point of using two features and hence we used just one cost. Now we have one column of X which is the cost and one column of y which is the execution time in ms.
3) After this, I standardised the data using min-max scaling. The reason for using min max scaling and not the standard normalisation is because, in min max scaling we will always end up getting values in the range of 0-1 while that is not the case in the other normalisation technique where we subtract the mean and then divide the standard deviation. Then, I did a log transformation of the cost variable X as the values of X were much more fluctuating in magnitude in the data.
3) After this, I trained a Linear Regression model and a Support Vector model on this data and found out the R2 scores and the Q error and I received a very bad score of 0.25 R2 and 565% on Q error. This suggested that the data was not yet linearly separable.
3) Plotting the data made it evident that the plot was tending towards a Gaussian distribution, following which I applied the following transformation to y to make the data linearly separable:

![](Aspose.Words.7c780c7e-dac6-4b09-91c6-d981ef049dca.003.png)

Plotting the data, we could understand that this data was linearly separable with a range(support vectors would run very good. The plot is as follows:

![](Aspose.Words.7c780c7e-dac6-4b09-91c6-d981ef049dca.004.png)

\6) Following this, I split the data to 90-10 ratio and then used Linear Regression and SVR model

as previously used to find the Q error and R2 score. Using these transformation, was super effective and ended up giving a 0.57 R2 for Linear Regression and 0.7 for SVR. The Q error for Linear regres- sion was 10.34% and 8.87% for SVR. Random Forest Regressors gave a similar result. Surprisingly, neural networks gave worse results than these classical models with a Q error of 23%. This code has not been included in the submission.![](Aspose.Words.7c780c7e-dac6-4b09-91c6-d981ef049dca.005.png)

Using SVR model makes the most sense as the data is linearly related with a given allowance perpendicular line and hence it is a good model to use in this case.

PART B - Bonus

For this bonus part, the major thing that I noticed, was that along with the cost of the work- load, the query itself should matter to the execution time. The complexity of the query should matter along with the databases used.

Thus to capture the complexity of the query I used the following procedures:

1) First, I imported the sql file present in the github repo and then read all the queries present in it. I did it using the following code:

![](Aspose.Words.7c780c7e-dac6-4b09-91c6-d981ef049dca.006.png)

2) Following this, I used a TF-IDF vectorizer setting a maximum number of features as 30 as its parameter. Choosing 30 means that, we shall get all the commands like Join, count, select along with the most common database names. Using more features can lead to entry of numbers that are not very useful.

![](Aspose.Words.7c780c7e-dac6-4b09-91c6-d981ef049dca.007.png)

3) Using this data along with the previous cost column in PART A, I applied the same models used in those cases and achieved a better Q-error of 8.42% using the Random Forest Regressor which gave 9.63% as its Q error previously.
3) I also saved the models as joblib files and uploaded them to the Github Repo

Conclusion

This task was on the building a learned cost model to accurately predict the execution time in milliseconds based on query runtime costs.

We found out that using other features such as the complexity of the query and the databases used, could significantly enhance the predictive accuracy of the model. Leveraging machine learning tech- niques, particularly the Support Vector Regression (SVR) model, proved to be effective in this task as the data followed a span across the linear relationship.

We also used TF-IDF method for this case. Using other pretrained Large language models like GPT-3 should give better results where we just input the queries and ask for an embedding vector which unfortunately I could not explore more. The trained models were also saved for future use, ensuring accessibility and reproducibility.
5

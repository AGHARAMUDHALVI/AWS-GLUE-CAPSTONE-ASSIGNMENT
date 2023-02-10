# AWS-GLUE-CAPSTONE-ASSIGNMENT
## capstone
## Authors
@agharamudhalvi

## Project Description
The goal of this project is to build a model that can predict whether a customer will default on a loan or make a deposit based on their historical financial data.
## Model Explanation
The dataset used in this project will likely consist of information such as the 
'age', 'job', 'marital', 'education', 'default', 'balance', 'housing', 'loan', 'contact', 'day', 'month', 'duration', 'campaign', 'pdays', 'previous', 'poutcome', 'deposit'. The model will be trained using supervised learning algorithms, such as   decision trees, random forests, or logistic regression, on a portion of the dataset  and then tested on the remaining data to evaluate its performance.
Once the model is trained and validated, it can be used by the bank to make informed decisions regarding loan approvals and marketing strategies.
Overall, the bank dataset classification model can help improve the efficiency and accuracy of the bank's decision-making process, and ultimately contribute to the growth and success of the bank.

## Schema
![image](https://user-images.githubusercontent.com/99899746/217865197-ae797e28-d718-442d-9073-182fcc325d58.png)


## To create an orchestration pipeline for training and inference in Apache Spark using AWS Glue, follow these steps:
step 1 : upload a CSV file into the source folder in Amazon S3.

step 2 : create AWS Glue crawler that creates the schema of the raw file from the stage folder in Amazon S3 and stores it in database.

step 3 : create a Glue job in the AWS Glue console.

step 4 : create a notebook in job and handle the dataset by reading it from the catalog inside the aws glue.

step 5 : An AWS Glue job transforms, compresses, and partitions the raw file into Parquet format.

step 6 : The AWS Glue job also moves the file to the transform folder in Amazon S3.

step 7 : created 2 job one for cleaning the dataset and another for training and inference

step 8 : Once jobs are created then I created triggers to automate the jobs 

step 9 : added all the triggers,jobs,crawlers in aws workflow to automate the pipeline run.

## created df for metrics and storing it in s3 for future reference
![image](https://user-images.githubusercontent.com/99899746/217865789-f5cf8362-9f40-4e2c-a6d2-f2b02e2a48b0.png)
![image](https://user-images.githubusercontent.com/99899746/217866051-26c3c1f1-e21d-487f-bcb9-633145a3a858.png)


## configurations
Define the job parameters, including the name of the job, the IAM role to be used, and the number of worker nodes.
Define the source data either by connecting to an Amazon S3 bucket or pointing to a file in the Glue data catalog.
Use Spark's data processing capabilities to clean and preprocess the data.
Train a machine learning model on the preprocessed data using the Spark MLlib library.

## stored the trained model in s3
![image](https://user-images.githubusercontent.com/99899746/217864786-7c31842b-8f34-4155-983e-d9cf025dbac1.png)

Store the trained model in an Amazon S3 bucket for later use.

## storing the processed data in amazon s3
![image](https://user-images.githubusercontent.com/99899746/217866371-aa7a56f8-0032-4c40-8888-d7756da0fb8a.png)


Define a new task in AWS Glue that performs inference using the stored model.
Connect the inference task to the output of the data processing stage to make predictions on new data.
Store the predictions in an Amazon S3 bucket or in the Glue data catalog.
Finally, monitor the performance of the pipeline and make necessary adjustments to optimize the accuracy of the predictions.

## Workflow-pipeline
![image](https://user-images.githubusercontent.com/99899746/217863925-92efb695-a701-4e94-9339-527ace0be020.png)
![image](https://user-images.githubusercontent.com/99899746/217864165-d4a83c27-3376-42f9-ac60-a36eb849e413.png)

## The above workflow runs as follows:

The bankdatastart-copy is the trigger created which runs the following steps automatically:
   create a crawler which help us to get the dataset from s3
   
   Bank datset-status will check wether the crawler is completed
   
   Then it allow us to create a job the data cleaning step 
   
   Bank job1-status will help us to check wether the previous job is completed
   
   Then it allow us to run next crawler which help us to load the cleaned data from s3 which is stored using the first job
   
   Bankdata cleaned-status helps us to check whether the crawler is completed
   
   Then it allow us to run the next job which is training and inference and store the output in s3.
   

This outline provides a general approach for creating an orchestration pipeline for training and inference in Apache Spark using AWS Glue, with the exact steps varying depending on the specific requirements of the use case.


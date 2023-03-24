# Udacity-Build-ML-Workflow-for-Scones-Unlimited-on-AWS-Sagemaker
**ML Workflow** is the notebook for this project.

This project is based on **CIFAR 100 dataset** to classify motorcycles and bicycles. This has 4 stages.

# 1) Data Staging:
Using Sage maker Studio, extracted the data from the hosting service (ETL process). Data is encoded in binary format and then transformed(decoded) into the correct shape and format, loaded data into S3 bucket.

# 2) Model Training and Deployment:
Used AWS build-in image classification algorithm to train the model. Trained model is then deployed to an endpoint and configured Model Monitor to track the deployment. Then made an inference to test the model endpoint.

# 3) Lambdas and Step Function Workflow:
Created three lambda functions: [lambda1.py](https://github.com/sukruta230901/Udacity-Build-ML-Workflow-for-Scones-Unlimited-on-AWS-Sagemaker/blob/main/lambda_functions/lambda1.py) is responsible for data generation. [lambda2.py](https://github.com/sukruta230901/Udacity-Build-ML-Workflow-for-Scones-Unlimited-on-AWS-Sagemaker/blob/main/lambda_functions/lambda2.py) is responsible for image classification. [lambda3.py](https://github.com/sukruta230901/Udacity-Build-ML-Workflow-for-Scones-Unlimited-on-AWS-Sagemaker/blob/main/lambda_functions/lambda3.py) is responsible for filtering out low-confidence inferences. And using Step Functions streamed the workflow of these lambda functions. It is exported as [step-function.json](https://github.com/sukruta230901/Udacity-Build-ML-Workflow-for-Scones-Unlimited-on-AWS-Sagemaker/blob/main/step_function/step-function.json)

# 4) Deploying, Testing and Evaluation:
Deployed model to an endpoint and performed several step function invocations for predictions using data from the test dataset. This process should has given me confidence that the workflow both succeeds AND fails as expected. In addition, used captured data from SageMaker Model Monitor to create a visualization to monitor the model.

# Screenshots of workflow:
Both the Workflow fail and success status with their respective event logs are stored in the [screenshots](https://github.com/sukruta230901/Udacity-Build-ML-Workflow-for-Scones-Unlimited-on-AWS-Sagemaker/tree/main/screenshots) folder of this repository.

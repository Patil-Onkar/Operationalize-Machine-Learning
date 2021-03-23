# Operationalizing Machine Learning

This project is a part of udacity nanodegree program. In this project, We will train and deploy a model on Azure cloud using AutoML feature of cloud. We will deploye it as a service and test its endpoint using python SDK. Further we can use this endpoint to any external API. We also create and publish ML pipeline, which automate the above process. At the end we will consume the pipeline endpoints. We have used bank marketing data as an example ml problem

## Architectural Diagram

In this project, We are going to create and publish ML pipeline. We have used bank marketing data as an example ml problem. Following is the step by step architetural diagram. [1]:
![image](https://user-images.githubusercontent.com/39105103/111894811-f9921e00-8a33-11eb-9251-a4b66b553367.png)

Step 1 Authentication: This step is required to authorize and authenticate users as well as developer of azure ML services.

Step 2 Auto ML Model: This is used to do feature engineering, model sampling and to select the best model (end-to-end ML process) automatically.

Step 3 Best Model Deployment: In this step we deploy the best model suitable for given data that we got from AutoML.

Step 4 Logging enable: Here we use azure’s Application Insight service to enable logging.


Step 5 Swagger Documentation: Swagger is a external tool. We use it here to understand the model endpoint.

Step 6 Model endpoint consumption: After deployment model creates endpoints. We can test or use the model using this endpoints.

Step 7 Creation and publishing of pipeline: We can Automate the above workflow by creating a azure pipeline and publish it.

Step 8: Documentation: It is required to understand the model architecture and its usage.  




## Key Steps

**AutoML Experiment**


The first step is to upload the data, apply machine learning techniques to the data and come p with best suitable data.Here we use AutoML feature of azure which automate the process and give us the best suitable model.


1. We need to provide either the dataset or a dataset uri. Here in this screenshot we can see that, dataset "BankMarketing_train" is uploaded.

![image](https://user-images.githubusercontent.com/39105103/111895314-afab3700-8a37-11eb-83e8-1d14ef2dc437.png)

2. Now, we initiate the AutoML and fed the uploaded data. The following screenshot shows that the AutoML experiment is completed.

![image](https://user-images.githubusercontent.com/39105103/111895346-eaad6a80-8a37-11eb-8ae6-6c44c730deb2.png)

3. Azure AutoML give us the best suitable model for given data. Best model can be seen as follows.  -:

![image](https://user-images.githubusercontent.com/39105103/111895398-55f73c80-8a38-11eb-9488-88690cebb8eb.png)




**Deploy Model and enable application insight**


In next step we deploy best model, Here we deployed best model, (i.e Voting Ensemble) using Azure Container Instance ACI. While deploying the instance, we set Authentication as "ON". And for recording the logs, we enabled Application Insight, we can do it while deploying the model or after the deployment. In our case we used *logs.py* python SDK script file to enable the application insight.

The following screenshots illustrate the deployement step.

1.screenshot shows the best model is deployed but Application insight isn't enabled yet.

![image](https://user-images.githubusercontent.com/39105103/111895526-2f85d100-8a39-11eb-89d8-8a59f6b3b77b.png)

2. After we run the script *logs.py*, Application Insight gets enabled as shown in below screenshot:

![image](https://user-images.githubusercontent.com/39105103/111895768-c1420e00-8a3a-11eb-9e1d-8b794ca62f07.png)

3. Screenshot shows the logs when we run the *logs.py* file.

![image](https://user-images.githubusercontent.com/39105103/111895796-f3ec0680-8a3a-11eb-9e65-c0b64a714974.png)


**Swagger Documentation**


Swagger is the tool that can be used to document the endpoints and understand how to use it. We run *swagger.sh* shell script to host the swagger API on our local machine and then run *serve.py* python script which connect our deployed model endpoints to swagger API. Then we can understand the 'request' format to our model endpoints.

Below screenshot will help us to understand the process in detail.


1. Swagger running on local host

![image](https://user-images.githubusercontent.com/39105103/111895864-8b515980-8a3b-11eb-9016-1d157c35a640.png)

2. Swagger - documenting deployed model

![image](https://user-images.githubusercontent.com/39105103/111895887-b045cc80-8a3b-11eb-91da-273718bb51ee.png)

![image](https://user-images.githubusercontent.com/39105103/111895899-c18ed900-8a3b-11eb-8a3f-8d543e04361c.png)

![image](https://user-images.githubusercontent.com/39105103/111895907-cfdcf500-8a3b-11eb-88ec-a85ab7b3e338.png)






**Consume Model Endpoint**



We have deployed the model on cloud and we use its endpoints as a service. This process is known as consume the model. Ideal way to consume a model endpoints is to use these endpoints into Web/mobile application API. But in our case we will use python SDK script *endpoint.py*, after we run *endpoint.py* script it sends a JSON request and displays the corresponding output.

Below screenshot illustrates the process.

1. Deployed model is consumed/used using python script endpoint.py. Screenshot shows its output

![image](https://user-images.githubusercontent.com/39105103/111895969-41b53e80-8a3c-11eb-9e2f-1cc795ac4620.png)







**Create,publish and consume a pipeline**


We can think of a pipeline as a object, which connects all the components and automate the workflow. Here we used jupyter notebook *aml-pipelines-with-automated-machine-learning-step.ipynb* to create,publish and consume the pipeline. As we run this jupyter notebook on azure ML studio, we use python SDK to create the pipeline, train it and then publish it.

Below screenshots Illustrates the process briefly. 

1. Pipeline section of Azure Machine learning studio. screenshot shows pipeline has been created:

![image](https://user-images.githubusercontent.com/39105103/111896073-07986c80-8a3d-11eb-96d6-a6ecfcb61bb4.png)

2. Following screenshot shows pipeline endpoints:

![image](https://user-images.githubusercontent.com/39105103/111896118-49c1ae00-8a3d-11eb-85f5-dde0f5b0d2a8.png)

3. Bankmarketing screenshot with automl modeule:

  3.1 Name of uploaded dataset is : BankMarketing Dataset

  ![image](https://user-images.githubusercontent.com/39105103/111896189-ae7d0880-8a3d-11eb-93c0-dba58483288d.png)

  3.2 Dataset with Automl module:

  ![image](https://user-images.githubusercontent.com/39105103/111896209-cc4a6d80-8a3d-11eb-84cd-8a119371b795.png)


4. Published Pipeline overview:

![image](https://user-images.githubusercontent.com/39105103/111896236-087dce00-8a3e-11eb-9510-50b708874df4.png)

Note that the status is ACTIVE. We can also see the endpoints URI

5. Jupyter notebook logs:

![image](https://user-images.githubusercontent.com/39105103/111903459-6de6b480-8a68-11eb-9920-987f886d3e6e.png)


![image](https://user-images.githubusercontent.com/39105103/111896368-0d8f4d00-8a3f-11eb-803c-c6f9c784ee61.png)

6. Rest Endpoint ML studio screenshot

![image](https://user-images.githubusercontent.com/39105103/111896421-8db5b280-8a3f-11eb-8544-6b4507dd69e5.png)


![image](https://user-images.githubusercontent.com/39105103/111896428-960ded80-8a3f-11eb-8ab9-cac844d6fdbe.png)







## Screen Recording
video link : https://drive.google.com/file/d/1KUSRI1ZxpLHKueV57Y79MVyzgNqzM6gs/view?usp=sharing


## Future Improvement suggestions:
There is lot more we can do and add in this project. We can integrate mobile cameras or speech recorders as IOT devices then use a machine learning problem such as object detection or language detection. For this kind of problems we can use/add services such as azure stream analytics and azure function. Creating and publishing pipeline which can incorporate this many services would be great fun. Again shouldn't ignore cost.

If we talk about this particular problem, we can create a webpage and consume pipeline endpoints. As we use this service we are going to generate more data and need to retrain and redeploy the model again. So, we can add a feature to our pipeline which can trigger this retraining and redeployment automatically.


### References 
[1]: Google Image Source: https://www.google.com/url?sa=i&url=https%3A%2F%2Fgithub.com%2Ftopics%2Fazure-machine-learning%3Fo%3Ddesc%26s%3Dupdated&psig=AOvVaw2FaTBo7wbvA096dVrPfM3h&ust=1616386299193000&source=images&cd=vfe&ved=0CAIQjRxqFwoTCKCB3c7DwO8CFQAAAAAdAAAAABAO

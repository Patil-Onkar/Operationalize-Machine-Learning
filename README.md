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
1. Upload the dataset to perform ML task

![image](https://user-images.githubusercontent.com/39105103/111895314-afab3700-8a37-11eb-83e8-1d14ef2dc437.png)

2. Experiment is completed.

![image](https://user-images.githubusercontent.com/39105103/111895346-eaad6a80-8a37-11eb-8ae6-6c44c730deb2.png)

3. Best model we got -:

![image](https://user-images.githubusercontent.com/39105103/111895398-55f73c80-8a38-11eb-9488-88690cebb8eb.png)




**Deploy Model and enable application insight**
1. Deployed model initial status (Application insight is not enabled)

![image](https://user-images.githubusercontent.com/39105103/111895526-2f85d100-8a39-11eb-89d8-8a59f6b3b77b.png)

2. Application insight is enabled now.

![image](https://user-images.githubusercontent.com/39105103/111895768-c1420e00-8a3a-11eb-9e1d-8b794ca62f07.png)

3. As we enabled using azure python SDK. Logs generated by the same.

![image](https://user-images.githubusercontent.com/39105103/111895796-f3ec0680-8a3a-11eb-9e65-c0b64a714974.png)

**Swagger Documentation**
1. Swagger running on local host

![image](https://user-images.githubusercontent.com/39105103/111895864-8b515980-8a3b-11eb-9016-1d157c35a640.png)

2. Swagger - documenting deployed model

![image](https://user-images.githubusercontent.com/39105103/111895887-b045cc80-8a3b-11eb-91da-273718bb51ee.png)

![image](https://user-images.githubusercontent.com/39105103/111895899-c18ed900-8a3b-11eb-8a3f-8d543e04361c.png)

![image](https://user-images.githubusercontent.com/39105103/111895907-cfdcf500-8a3b-11eb-88ec-a85ab7b3e338.png)






**Consume Model Endpoint**

1. Deployed model is consumed/used using python script endpoint.py. Screenshot shows its output

![image](https://user-images.githubusercontent.com/39105103/111895969-41b53e80-8a3c-11eb-9e2f-1cc795ac4620.png)







**Create,publish and consume a pipeline**

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

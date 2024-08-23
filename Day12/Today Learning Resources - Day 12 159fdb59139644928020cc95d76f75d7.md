# Today Learning Resources - Day 12

## **Amazon Bedrock Overview**

Amazon Bedrock is a service from Amazon Web Services (AWS) designed to facilitate the development and deployment of generative AI applications. It grants developers access to a variety of **foundation models**—large AI models trained on extensive datasets capable of performing diverse tasks. These foundation models act as the backbone for creating innovative AI applications.

For detailed pricing information, please refer to the [Amazon Bedrock Pricing](https://aws.amazon.com/bedrock/pricing/) page.

Follow this video: [Watch here](https://youtu.be/2maPaQutcWs?si=KPo22Lb4iIq8iAOu)

## **Creating an IAM User**

To get started with Amazon Bedrock, follow these steps to create an IAM user:

1. Navigate to the IAM section in your AWS Management Console.
2. Click on **Create User**.
3. Attach the **Administrator Access** policy.
4. Save the user details and proceed to create and download the access key.

Next, configure your AWS CLI with the access key and secret access key. After configuration, request access to the model in AWS Bedrock for your specified region.

## **Deploying Hugging Face Open Source LLM Models in AWS SageMaker**

### **Introduction to Amazon SageMaker**

Amazon SageMaker is a cloud-based service that streamlines the process of building, training, and deploying machine learning (ML) models. It is designed to be user-friendly, enabling data scientists and developers to work efficiently without the need to manage the underlying infrastructure.

Follow this video: [Watch Here](https://youtu.be/U72q95dHpRo?si=-j3FhuaSt3YXp6wA)

### **Setting Up Amazon SageMaker**

To deploy models using Amazon SageMaker, follow these steps:

1. Navigate to **Amazon SageMaker** in the AWS Management Console.
2. Go to **Domains** and click on **Create Domain**.
3. Set up your SageMaker Domain. First, create a VPC with one subnet. The status should initially be in a pending state.
4. Once the status changes to **InService**, go to the **User Section** to create a user. Select the user and click on **Launch**.

### **Creating a JupyterLab Space**

1. Open **SageMaker Studio**.
2. Select **JupyterLab**.
3. Click on **Create JupyterLab Space**, specify a name, and create the space.

For pricing details, visit the [Amazon SageMaker Pricing](https://aws.amazon.com/sagemaker/pricing/?p=pm&c=sm&z=4) page.

### **Configuring the JupyterLab Environment**

1. Select the instance type: **ml.m5.2xlarge**.
2. Allocate storage: **10 GB**.
3. Click on **Run Space** to create your space.
4. Open JupyterLab and select **Python**.

### **Running Your Code**

To verify the deployment of your model, run the code available at this [GitHub repository](https://github.com/SaiKumarSeela/GenAI_on_AWSCloud/tree/main/AWSSagemaker).

### **Testing the Model Deployment**

To check if your model is deployed:

1. Go to **Studio**.
2. Click on **Deployments**.
3. Select **Endpoints** and choose your endpoint.
4. Test the model by passing a query and observing the response.

### **Cleaning Up AWS SageMaker**

For guidance on cleaning up your AWS SageMaker environment, watch this tutorial: [Clean AWS SageMaker](https://youtu.be/5LjpO_xoQ2M?si=Isc7uPDBhLCtCMp4).
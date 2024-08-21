# Today Learning Resource - Day 10

## **End-to-End Blog Generator Project on AWS Using AWS Bedrock and AWS Lambda:**

Project Workflow: [Watch this video](https://youtu.be/3OP39y4dO_Y?si=2fegvBJFSWqwu56U)

![AWSProjectWorkflow.png](Today%20Learning%20Resource%20-%20Day%2010%2082cd635020cd41b0bffa3078a46125de/AWSProjectWorkflow.png)

## Grant Access to the Specified Models in AWS Bedrock

Navigate to **Amazon Bedrock** > **Model Access** > Select the desired models and grant access.

**AWS Lambda**: AWS Lambda is a compute service that executes your code in response to events and automatically manages the compute resources, providing a rapid way to transform an idea into a modern, production-ready serverless application.

## Create a Lambda Function

1. Search for **Lambda** in AWS.
2. Click on **Create Function**, select “**Author from Scratch**,” and fill in the basic information:
    - **Function name**: awsappbedrock (or any name of your choice)
    - **Runtime**: Python 3.12 (the latest version)
    - **Architecture**: x86_64 (leave the remaining settings as default)

Next, scroll down to **Configurations** > **General Configuration** > click **Edit** and set the **Timeout** to 3 minutes.

## Trigger the Lambda Function

To trigger the Lambda function, you will need to write Python code.

Open **VS Code** or any IDE, and follow these steps:

1. Create a Python environment using the following commands:
    - `python -m venv <env_name>`
    - `env_name\\Scripts\\activate.bat`
2. Write your code in the Lambda function: [*View Code*.](https://github.com/SaiKumarSeela/GenAI_on_AWSCloud)
3. Click on **Deploy** to save your changes.
4. Create a layer to install the latest version of **boto3**:
    - First, create a zip file. Run this command in your terminal:
        - `pip install boto3 -t python/` and then compress that folder into a zip file.
5. Click on **Layers** > **Create Layer** > specify a name, upload the zip file you created, and select the compatible runtime (Python 3.12, 3.10, 3.11).
6. Select your function, scroll to the bottom, click **Add Layer** > **Custom Layer**, select the layer, and click **Add**.

## Create an API Gateway

1. Click on **HTTP API** > specify a name > click **Create**.
2. Add Routes > **Create Route** > select the **POST** method and give it a name > attach integration > select the Lambda function > click **Create**.
3. Under **Stages**, specify a name > click **Create** > open **Stages** > click **Deploy** and select the environment > copy the invoke URL and save it.

## Create an S3 Bucket

1. Go to **S3** > click on **Create Bucket** > give the bucket a unique name > click **Create**.
2. Open **Postman**, paste the invoke URL obtained from stages, and append the route. In the body, select **raw** and write:
    
    ```json
    {
        "blog_topic": "Machine Learning"  // or any topic of your choice
    }
    
    ```
    

If you encounter an "Access Denied" error while checking the logs of the Lambda function in CloudWatch:

1. Navigate to **Permissions** in Lambda > select the role name > attach **Administrator Access**.
2. Reload the Lambda page to confirm that permissions have changed.

Now, run the function again. You should see the response: “Blog is completed.” Check the logs in CloudWatch to verify that the blog has been successfully stored in the S3 bucket you created earlier.
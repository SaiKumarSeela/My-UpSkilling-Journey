# Today Learning Resources - Day 11

## **End To End Advanced RAG App Using AWS Bedrock And Langchain**

Project workflow: [Watch Here](https://youtu.be/0LE5XrxGvbo?si=Lsk-46yLCSTThZBr)

My github Code: [View Code Here](https://github.com/SaiKumarSeela/GenAI_on_AWSCloud/tree/main/RAGusingAWSBedrock)

![image.png](Today%20Learning%20Resources%20-%20Day%2011%20cb7ce4304af54c6a9863f8ca1003314a/image.png)

### **AWS Configuration**

- **Grant Model Access**:
    - Navigate to **Amazon Bedrock** within the AWS Management Console.
    - Go to **Model Access** and select the models you want to use, such as Llama3.
    - Ensure access is granted to these models so they can be used in your application.
- **Set Up AWS Credentials**:
    - Ensure that your AWS credentials are configured correctly on your local machine or server.
    - Set the **AWS Access Key ID** and **AWS Secret Access Key** in your environment variables or AWS configuration files.
    - Set the region to `ap-south-1`, which matches the region specified in your project.

### **Project Setup**

- **Python Environment Setup**:
    - Create a virtual environment in your IDE (e.g., VS Code).
    - Activate the virtual environment and install necessary dependencies like `boto3`, `Streamlit`, and other required libraries.

### **Document Ingestion**

- **Load PDF Documents**:
    - Use a document loader to scan and load all PDF files from a specified directory.
    - The loader will handle multiple PDFs, preparing them for processing.
- **Split Text for Processing**:
    - Implement a text splitter to break down large PDF documents into smaller, manageable text chunks.
    - This ensures that the text data is easier to work with and retrieve relevant information from during queries.

### **Vector Embedding and Storage**

- **Generate Vector Embeddings**:
    - Convert the text chunks into vector embeddings using a generative AI model.
    - These embeddings represent the textual information in a numerical format, making it easier for the model to understand and process.
- **Store Embeddings in FAISS**:
    - Store the generated vector embeddings in a FAISS index.
    - FAISS allows for efficient similarity search, enabling quick retrieval of relevant text chunks when a query is made.

### **Model Integration**

- **Initialize Llama3 Model**:
    - Use the AWS Bedrock service to initialize the Llama3 model.
    - This model will process the queries made by users, leveraging the vector embeddings stored in the FAISS index.

### **Streamlit Interface**

- **User Interaction Setup**:
    - Develop a web-based interface using Streamlit where users can input questions and interact with the system.
    - The interface will have options to update the vector store when new PDFs are added and to query the Llama3 model for answers.

### **Running the Application**

- **Launch the Application**:
    - Run the Streamlit application to start the web interface.
    - Users can now interact with the system, ask questions based on the PDF documents, and receive responses generated by the Llama3 model on AWS Bedrock.
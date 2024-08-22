# Today Learning Resources - Day 5

# Explore RAG Pipelines:

![RagPipeline.png](Today%20Learning%20Resources%20-%20Day%205%20d246a67fba7749f6a58a1889856dcf1b/RagPipeline.png)

**Chains:** [Chains](https://python.langchain.com/v0.1/docs/modules/chains/) refer to sequences of calls - whether to an LLM, a tool, or a data preprocessing step. The primary supported way to do this is with [LCEL](https://python.langchain.com/v0.1/docs/expression_language/).

**Retrievers**: A [retriever](https://python.langchain.com/v0.1/docs/modules/data_connection/retrievers/) is an interface that returns documents given an unstructured query. It is more general than a vector store. A retriever does not need to be able to store documents, only to return (or retrieve) them. Vector stores can be used as the backbone of a retriever, but there are other types of retrievers as well.

**Retrieval chain:** This [chain](https://python.langchain.com/docs/modules/chains/) takes in a user inquiry, which is then
passed to the retriever to fetch relevant documents. Those documents
(and original inputs) are then passed to an LLM to generate a response

![Retriever.png](Today%20Learning%20Resources%20-%20Day%205%20d246a67fba7749f6a58a1889856dcf1b/Retriever.png)

- **Agents**: The core idea of [agents](https://python.langchain.com/v0.1/docs/modules/agents/) is to use a language model to choose a sequence of actions to take. In chains, a sequence of actions is hardcoded (in code). In agents, a language model is used as a reasoning engine to determine which actions to take and in which order.
- Opensource llms as Agents: https://huggingface.co/blog/open-source-llms-as-agents
- **Groq:** [Groq(opens in a new tab)](https://groq.com/) recently made a lot of headlines as one of the fastest LLM inference solutions available today. There is a lot of interest from LLM practitioners to reduce the latency in LLM responses. Latency is an important metric to optimize and enable real-time AI applications. There are many companies now in the space competing around LLM inference.  https://www.promptingguide.ai/research/groq

**Problem Faced:** Got this error while running hugging face, the problem is in pytorch library, “OSError: [WinError 126] The specified module could not be found. one of its dependencies”

Solution: https://www.youtube.com/watch?v=-ky896Qp1k8

## RAG Pipelines with Different Tools:

- Langchain, ChromaDB, and FAISS: https://youtu.be/9Thc6hRw2Gs?si=dKGScIhJzSNaMH99
- Lanchain chain and Retrievers: https://youtu.be/tIwi92nkcu0?si=jM78JyhR65HEbow3
- Multiple DataSources (wikipedia,langsmith,arxiv ):  https://youtu.be/2_gSXyt2108?si=TB_JwKwQ-E7IymQR
- Opensource llms, Groq inference engine: https://youtu.be/QQdiHrIc84o?si=Et6pcgzFQW9Ovma9
- Huggingface, MistralAi: https://youtu.be/RZ2Vu8z-P1Q?si=XR8k2Jhu9sYW9pot
- Groq API, Llama3: https://youtu.be/-PSq_ilkvwI?si=yKWH2SSIKJFiqCtS
- Astra DB, Huggingfacce: https://youtu.be/8Vq4K1EGq2g?si=A4J7HJKQX7_7uKlF
- ObjectBox Vecor Database: https://youtu.be/TcvI-Nnebow?si=hNq94fa4MEcZEOOF
- Experimented langchain-huggingface library: https://youtu.be/T6XhRFeDbPY?si=gHu_e0jOQxfc9Qek
- Gemma and Groq API: https://youtu.be/LOUaom9HZIg?si=XnOxlRQm4LXPFxDz
- Finally, Hybrid search, Pinecone Vector DB: https://youtu.be/CK0ExcCWDP4?si=DCaONxLLMF9Q4Jh1

## **Steps to Build RAG Systems**

Building a Retrieval-Augmented Generation (RAG) system involves several key steps. Below is a detailed, step-by-step process to guide you through the implementation.

## **1. Data Ingestion**

- **Read the PDF Document**: Use **`PyPDFLoader()`** to read the PDF document and extract text.

## **2. Document Loading**

- **Load the Document**: Ensure the document is properly loaded into your system for further processing.

## **3. Chunk Creation**

- **Split the Text into Chunks**: Utilize **`RecursiveCharacterTextSplitter()`** to divide the text into manageable chunks for easier processing.

## **4. Generate Embeddings**

- **Generate Vector Representations**:
    - Experiment with different embedding models such as:
        - **`HuggingFaceEmbeddings`**
        - **`OpenAIEmbeddings`**
        - **`OllamaEmbeddings`**
        - **`GooglePalmEmbeddings`**

## **5. Store Embeddings in Vector Database**

- **Store in Vector Database**: Use **`FAISS.from_documents(docs, embeddings)`** to store the generated embeddings in a vector database.

## **6. Query Using Similarity Search**

- **Perform Similarity Search**: Use the command **`db.similarity_search(query)`** to retrieve relevant chunks based on a user query.

## **7. Create a Retriever**

- **Establish a Retriever Interface**: Create a retriever that connects to the language models (LLMs) using **`db.as_retriever()`**.

## **8. Create LLM**

- **Experiment with LLM Invocation**: Use **`llm.invoke()`** to run LLM models locally. You can leverage the Hugging Face pipeline for this purpose.

## **9. Create a Prompt Template**

- **Define the Prompt Template**: Use **`PromptTemplate(template, input_variables=['a', 'b'])`** to create a structured prompt for the LLM.

## **10. Set Up RetrievalQA**

- **Configure RetrievalQA**: Use **`RetrievalQA.from_chain_type(llm, type, retriever, prompt)`** to set up the retrieval-based question-answering system.

## **11. Experiment with RetrievalQA Invocation**

- **Test RetrievalQA**: Invoke the retrieval QA system using **`retrievalQA.invoke()`** to evaluate its performance and refine as necessary.

## Hybrid Search RAG:

![HybridSearch.png](Today%20Learning%20Resources%20-%20Day%205%20d246a67fba7749f6a58a1889856dcf1b/HybridSearch.png)

How it works:

![HowHybridSearchWorks.png](Today%20Learning%20Resources%20-%20Day%205%20d246a67fba7749f6a58a1889856dcf1b/HowHybridSearchWorks.png)

**Reciprocal Rank Fusion (RRF)**:  [https://medium.com/@sowmiyajaganathan/hybrid-search-with-re-ranking-ff120c8a426d](https://medium.com/@sowmiyajaganathan/hybrid-search-with-re-ranking-ff120c8a426d)

- My github repository:  https://github.com/SaiKumarSeela/Explore-Langchain
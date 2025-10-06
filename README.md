# ⚡ High-Speed RAG System with Groq, LangChain, and Streamlit

This project demonstrates a flexible and incredibly fast Retrieval-Augmented Generation (RAG) system. It leverages the speed of the **Groq API** for large language model (LLM) inference, **LangChain** for RAG pipeline orchestration, and **Streamlit** for an interactive web interface.

## 🚀 Key Features

* **Ultra-Fast Inference:** Utilizes the Groq API to run cutting-edge models like **Llama 3 8B** and **Mixtral 8x7B** at peak speed.

* **Flexible Data Ingestion:** Includes configurations for loading data from **Web URLs** (`app.py`) and **Local PDF Directories** (`llama3.py`).

* **Vector Store Variety:** Demonstrates using **FAISS** for simple, local vector storage, and **Cassandra (Astra DB)** in the notebook for a scalable, cloud-native vector store.

* **Multiple Embeddings:** Supports both **Ollama Embeddings** (requiring a local Ollama server) and **OpenAI Embeddings**.

## ⚙️ Project Structure

| File | Description | Core Components | 
 | ----- | ----- | ----- | 
| `app.py` | Streamlit RAG app. Loads data from a web URL, uses **Ollama Embeddings**, and **FAISS**. Uses Mixtral 8x7B. | Streamlit, WebBaseLoader, OllamaEmbeddings, FAISS | 
| `llama3.py` | Streamlit RAG app. Loads data from a local directory (`./us_census`), uses **OpenAI Embeddings**, and **FAISS**. Uses Llama 3 8B. | Streamlit, PyPDFDirectoryLoader, OpenAIEmbeddings, FAISS | 
| `groq.ipynb` | Jupyter Notebook demonstrating scalable RAG using **Cassandra (Astra DB)** as the vector store. | Jupyter, Cassio, Cassandra/Astra DB, Groq | 

## 🛠️ Setup and Installation

### 1. Prerequisites

You will need the following accounts/tools:

* **Python 3.x**

* **Groq API Key:** For running the LLMs.

* **OpenAI API Key:** Required for `llama3.py` (for the embeddings).

* **Ollama:** If running `app.py`, you must have **Ollama installed and running** with the desired embedding model (e.g., `nomic-embed-text`) locally.

* **Astra DB Credentials:** If running the `groq.ipynb` notebook (Application Token and Database ID).

* **PDF Data:** For `llama3.py`, create a folder named `us_census` in the root directory and place your PDF files inside it.

### 2. Environment Setup

1. **Clone the repository (or ensure files are in one directory):**

   ```
   # If using Git
   git clone <your-repo-link>
   cd <your-repo-name>
   
   ```

2. **Install dependencies:**
   You will need a few different libraries to cover all the file requirements (web loading, PDF handling, vector databases).

   ```
   pip install streamlit langchain-groq langchain-openai langchain-community faiss-cpu python-dotenv pypdf cassio
   
   ```

3. **Configure Environment Variables:**

   Create a file named **`.env`** in the root directory and add your API keys. The code is configured to load these automatically.

   ```
   GROQ_API_KEY="YOUR_GROQ_API_KEY_HERE"
   OPENAI_API_KEY="YOUR_OPENAI_API_KEY_HERE"
   
   # Required for groq.ipynb/Cassandra setup
   # ASTRA_DB_APPLICATION_TOKEN="YOUR_ASTRA_DB_APPLICATION_TOKEN_HERE"
   # ASTRA_DB_ID="YOUR_ASTRA_DB_ID_HERE"
   
   ```

## ▶️ Running the Applications

### A. Streamlit Web Applications

You can run either application to test different RAG pipelines.

1. **To run the Web Loader (Ollama Embeddings) App:**

   ```
   streamlit run app.py
   
   ```

2. **To run the Local PDF Loader (OpenAI Embeddings) App:**

   * **IMPORTANT:** Ensure you have the `us_census` directory with PDFs available.

   * Run the application:

     ```
     streamlit run llama3.py
     
     ```

3. Access the web application in your browser (usually `http://localhost:8501`).

### B. Jupyter Notebook (Cassandra/Astra DB)

1. Start your Jupyter environment (e.g., JupyterLab or VS Code Notebook).

2. Open **`groq.ipynb`**.

3. Ensure your **Astra DB credentials** are set in your `.env` file.

4. Run the cells sequentially to initialize the connection, load the document, create the Cassandra vector store, and perform the RAG query.

This setup should allow you to showcase the speed and flexibility of using Groq with various LangChain components! Let me know if you need any section elaborated or adjusted.
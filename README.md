# 💹 FinEdge RAG Chatbot

**FinEdge** is an intelligent, conversational AI assistant designed for financial analysis. It leverages a Retrieval-Augmented Generation (RAG) pipeline to answer questions based *only* on a provided set of financial documents. This chatbot provides precise answers, cites the exact source page for verification, and maintains a professional, analytical tone throughout the conversation.

## 🌟 Key Features

* **Conversational AI with Memory**: Remembers previous parts of the conversation for context-aware follow-up questions.
* **Source Verification**: Displays an image of the exact page from the source PDF document, allowing users to instantly verify the information.
* **Secure & Private**: Operates exclusively on the documents you provide, ensuring your data remains private and the AI doesn't use external knowledge.
* **Professional Persona**: The AI is prompted to act as a highly knowledgeable financial analyst, ensuring professional and relevant responses.
* **Interactive UI**: A clean, user-friendly chat interface built with Streamlit.

## 🛠️ Technology Stack

* **Backend**: Python
* **AI/ML Framework**: LangChain
* **LLM**: Google Gemini (`gemini-1.5-flash-latest`)
* **Embeddings**: Hugging Face `sentence-transformers`
* **Vector Store**: FAISS (Facebook AI Similarity Search)
* **Frontend**: Streamlit
* **PDF Processing**: PyMuPDF (`fitz`)
* **Environment Management**: `python-dotenv`

## ⚙️ How It Works

The application follows a Retrieval-Augmented Generation (RAG) architecture:

1.  **Ingestion**: PDF documents in the `/data` directory are loaded, split into smaller, overlapping chunks, and converted into numerical vectors (embeddings).
2.  **Indexing**: These embeddings are stored in a FAISS vector store for efficient similarity searching.
3.  **Retrieval**: When a user asks a question, the system converts the query into an embedding and retrieves the most relevant document chunks from the vector store.
4.  **Generation**: The user's question, the conversation history, and the retrieved document chunks are passed to the Gemini LLM with a detailed prompt.
5.  **Response**: The LLM generates a professional answer based *only* on the provided context and the chatbot displays the answer along with the source document pages.

## 🚀 Getting Started

Follow these steps to set up and run the project on your local machine.

### Prerequisites

* Python 3.9+
* A Google API Key. You can get one from the [Google AI Studio](https://aistudio.google.com/app/apikey).

### Installation

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/omhome16/FinEdge-RAG-chatbot.git](https://github.com/omhome16/FinEdge-RAG-chatbot.git)
    cd FinEdge-RAG-chatbot
    ```

2.  **Create a virtual environment and activate it:**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3.  **Install the required dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Set up your environment variables:**
    * Create a file named `.env` in the root directory of the project.
    * Add your Google API key to this file:
        ```
        GOOGLE_API_KEY="YOUR_GOOGLE_API_KEY_HERE"
        ```

5.  **Add your documents:**
    * Place all the PDF files you want to chat with inside the `data/` directory.

### Usage

1.  **Process your documents and create the vector store:**
    * Run the ingestion script. This only needs to be done once, or whenever you add, remove, or change the documents in the `data/` folder.
    ```bash
    python load_and_process_docs.py
    ```

2.  **Launch the chatbot application:**
    ```bash
    streamlit run app.py
    ```
    Open your web browser and navigate to the local URL provided by Streamlit (usually `http://localhost:8501`).

## 🔮 Future Improvements

* **Fine-Tuning**: Fine-tune a smaller open-source model on financial text to capture an even more specialized tone and understanding.
* **Advanced Retrieval**: Implement a re-ranking mechanism to improve the quality of retrieved documents before they are sent to the LLM.
* **Deployment**: Containerize the application with Docker and deploy it to a cloud service like Streamlit Community Cloud or Hugging Face Spaces.

## 📄 License

This project is licensed under the MIT License. See the `LICENSE` file for more details.

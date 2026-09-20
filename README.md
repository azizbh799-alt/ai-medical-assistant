# 🩺 AI Medical Assistant — CareChat

An AI-powered medical assistant built using **Retrieval-Augmented Generation (RAG)** to provide context-aware answers based on a medical knowledge base.

The application combines **LangChain, Pinecone, Hugging Face embeddings, Ollama/Phi-3 and Flask** to build an end-to-end RAG application.

> ⚠️ **Disclaimer:** This project is for educational and demonstration purposes only. It is not intended to provide medical diagnosis or replace professional medical advice.

---

## 🚀 Project Overview

CareChat is a conversational AI application that allows users to ask questions related to medical information.

Instead of relying only on the language model's internal knowledge, the application retrieves relevant information from a medical document stored in a vector database and uses that context to generate the response.

### RAG workflow

```text
                    User
                      │
                      ▼
              CareChat Web UI
                      │
                      ▼
                Flask Backend
                      │
                      ▼
                  LangChain
                      │
             ┌────────┴────────┐
             │                 │
             ▼                 ▼
        Pinecone            Ollama
       Vector DB             Phi-3
             │                 │
             └────────┬────────┘
                      │
                      ▼
                AI Response
```

---

## ✨ Features

* 💬 Interactive AI medical chatbot
* 🔎 Retrieval-Augmented Generation (RAG)
* 📚 Medical document knowledge base
* 🧠 Hugging Face sentence embeddings
* 🗄️ Pinecone vector database
* 🤖 Local LLM inference with Ollama and Phi-3
* 🔗 LangChain-based retrieval pipeline
* 🌐 Flask backend
* 💻 Responsive web interface
* 🔐 Environment-based API key configuration

---

## 🛠️ Technologies

| Technology              | Purpose                 |
| ----------------------- | ----------------------- |
| Python                  | Application development |
| Flask                   | Web backend             |
| LangChain               | RAG orchestration       |
| Pinecone                | Vector database         |
| Hugging Face            | Text embeddings         |
| Sentence Transformers   | Document embeddings     |
| Ollama                  | Local LLM runtime       |
| Phi-3                   | Language model          |
| HTML / CSS / JavaScript | Frontend                |
| Git / GitHub            | Version control         |

---

## 📂 Project Structure

```text
ai-medical-assistant/
│
├── data/
│   └── Medical_book.pdf
│
├── research/
│
├── src/
│   ├── helper.py
│   └── prompts.py
│
├── static/
│
├── templates/
│   └── chat.html
│
├── .github/
│
├── app.py
├── store_index.py
├── settings.py
├── Dockerfile
├── requirements.txt
├── README.md
├── LICENSE
└── .gitignore
```

---

# ⚙️ Installation

## 1. Clone the repository

```bash
git clone https://github.com/azizbh799-alt/ai-medical-assistant.git
cd ai-medical-assistant
```

---

## 2. Create a virtual environment

### Windows

```powershell
python -m venv venv
venv\Scripts\activate
```

### Linux / macOS

```bash
python3 -m venv venv
source venv/bin/activate
```

---

## 3. Install dependencies

```bash
pip install -r requirements.txt
```

---

# 🔑 Configuration

Create a `.env` file in the root directory:

```env
PINECONE_API_KEY=your_pinecone_api_key
```

Never commit your `.env` file or expose your API keys publicly.

The `.env` file is excluded through `.gitignore`.

---

# 🤖 Configure Ollama

Install Ollama and download the Phi-3 model:

```bash
ollama pull phi3
```

Verify that the model is available:

```bash
ollama list
```

You can also test it with:

```bash
ollama run phi3
```

---

# 🗄️ Create the Pinecone Vector Index

The project uses a medical PDF as the knowledge source.

The document is processed through the following pipeline:

```text
Medical PDF
    ↓
Document Loading
    ↓
Text Splitting
    ↓
Hugging Face Embeddings
    ↓
Vector Representations
    ↓
Pinecone
```

Run:

```bash
python store_index.py
```

This creates/populates the `medical-chatbot` Pinecone index.

> The first execution may take some time because the embedding model needs to be downloaded and the document needs to be processed.

---

# ▶️ Run the Application

Start the Flask application:

```bash
python app.py
```

The application runs locally at:

```text
http://127.0.0.1:5001
```

Open the URL in your browser and start chatting with CareChat.

---

# 💬 Example Questions

You can test the application with questions such as:

```text
What are the common symptoms of type 2 diabetes?
```

```text
What are the main risk factors for type 2 diabetes?
```

```text
What lifestyle changes are generally recommended for people at risk?
```

```text
What information is available about diabetes management?
```

---

# 🧠 How RAG Works in This Project

The application follows a Retrieval-Augmented Generation architecture.

### 1. Document ingestion

The medical PDF is loaded and processed.

### 2. Text splitting

The document is divided into smaller chunks to make retrieval more efficient.

### 3. Embedding generation

Each chunk is transformed into a numerical vector using a Hugging Face sentence-transformer model.

### 4. Vector storage

The embeddings are stored in **Pinecone**.

### 5. User query

When a user asks a question, the query is converted into an embedding.

### 6. Similarity search

Pinecone retrieves the most relevant document chunks.

### 7. Context + LLM

The retrieved information is provided as context to the Phi-3 language model through LangChain.

### 8. Response

The model generates the final answer based on the retrieved context.

```text
User Question
      ↓
Query Embedding
      ↓
Pinecone Similarity Search
      ↓
Relevant Medical Documents
      ↓
LangChain
      ↓
Phi-3 / Ollama
      ↓
Generated Answer
```

---

# 🎨 User Interface

The application includes a custom conversational interface designed for a simple and professional user experience.

Main interface features:

* Clean medical assistant dashboard
* Conversation interface
* AI response indicators
* New conversation button
* Responsive design
* Medical AI disclaimer

---

# 🔐 Security Considerations

API credentials are stored using environment variables.

Example:

```env
PINECONE_API_KEY=your_api_key
```

The following files/directories should not be committed:

```text
.env
venv/
__pycache__/
```

Never expose API keys in source code, GitHub repositories or screenshots.

---

# 📌 Project Background

This project was initially based on an open-source implementation.

I used the project as a foundation to understand and work with **RAG-based LLM applications**, then adapted and extended the application by configuring the RAG pipeline, integrating Pinecone, working with Hugging Face embeddings and Ollama, and redesigning the user interface.

The project was developed as a practical learning project focused on **Generative AI, RAG, vector databases and cloud-oriented application architecture**.

---

# 🎯 Learning Objectives

Through this project, I worked on:

* Understanding RAG architecture
* Working with Large Language Models
* Using vector databases
* Generating and managing embeddings
* Integrating LangChain
* Working with Pinecone
* Running LLMs locally with Ollama
* Building APIs with Flask
* Developing a conversational web interface
* Managing environment variables and API credentials
* Understanding AI application deployment concepts

---

# 🚧 Future Improvements

Possible future improvements include:

* ☁️ AWS deployment
* 🐳 Docker containerization
* 🔐 HTTPS and secure API configuration
* 👤 User authentication
* 💾 Conversation history
* 📊 Monitoring and logging
* ⚡ Streaming AI responses
* 🧠 Support for additional medical documents
* 🔄 CI/CD pipeline
* 🛡️ AI security and prompt-injection protection

---

# 📄 License

This project follows the license included in the repository.

Please refer to [`LICENSE`](LICENSE) for the applicable terms.

---

## 👨‍💻 Author

**Mohamed Aziz Becheikh**

Full Stack Developer | Cloud & DevSecOps Enthusiast

GitHub:
https://github.com/azizbh799-alt

---

⭐ If you find this project useful, feel free to explore the repository and follow the development.

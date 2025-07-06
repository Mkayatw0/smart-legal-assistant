# Smart Legal Assistants using Retrieval Augmented Generation (RAG)
A scalable, beginner-friendly application for answering legal questions using a document knowledge base with Retrieval-Augmented Generation (RAG).

## What is RAG?
Retrieval-Augmented Generation (RAG) is an advanced technique in NLP that combines two key components:

Retrieval: Finds relevant content (e.g., from your uploaded documents).

Generation: Uses a language model (like GPT) to generate a contextual answer based on the retrieved content.

This ensures responses are:

Grounded in facts

Transparent with references

Scalable to your custom knowledge base

## Project Purpose
To help legal teams or individuals query legal documents in natural language, getting accurate, reference-backed responses — with a user-friendly interface and easily configurable backend.

Even junior data scientists can run, extend, or deploy this project.

## Features
 Document Retrieval: Uses vector search (e.g., via Pinecone) to locate the most relevant documents.

 Modular Pipeline: Each stage (embedding, retrieval, generation) is customizable.

 Customizable Prompts: Easily change how the model responds using templates.

 Query Enhancement: Optional query expansion + reranking logic to improve relevance.

 Streamlit UI: Clean, interactive frontend for querying and feedback.

 Deployment Ready: Works with Docker or Render for one-click cloud hosting.

## Technologies Used
**Tool**	**Purpose**
**Python**:	Main programming language
**Streamlit**:	Web app interface
**Pinecone**:	Vector database for semantic search
**OpenAI/TogetherAI**:	Large language models for response generation
**Docker**:	Containerization for consistent deployment

## Code Structure

smart-legal-assistants/
├── src/SmartLegalAssistant/
│   ├── core/               # Main logic: LLMs, embeddings, retrievers
│   ├── streamlit_app/      # Streamlit frontend
│   └── utils/              # Helpers: logger, prompts, error handling
├── Dockerfile              # Docker config
├── requirements.txt        # Python dependencies
├── render.yaml             # Render.com deployment file
├── .env                    # API key and environment variables

## Getting Started (Step-by-Step)
### Prerequisites
Make sure you have:

Python ≥ 3.8

pip (Python package manager)

Git

API Keys for:

Together.ai

Pinecone

### 1. Clone the Repository
git clone https://github.com/yourusername/rag-assistant.git
cd rag-assistant
### 2. Set Up Environment Variables
Create a .env file in the root:

```
TOGETHER_API_KEY=your_together_api_key
PINECONE_API_KEY=your_pinecone_api_key
PINECONE_ENVIRONMENT=your_pinecone_environment
PINECONE_INDEX_NAME=your_pinecone_index_name
PINECONE_NAMESPACE=optional_namespace
```

These control the external services your app connects to.

### 3. Install Dependencies

pip install -r requirements.txt

This installs all required Python libraries — including: openai, pinecone-client, streamlit, sentence-transformers

### 4. Run the App Locally

streamlit run src/SmartLegalAssistant/streamlit_app/main.py
Visit http://localhost:8501 in your browser to use the app.

### Docker Deployment
Prefer containerization? Here’s how:

1. Build the Image
docker build -t rag-assistant .

2. Run the App
docker run -p 8501:8501 --env-file .env rag-assistant

This ensures consistency across environments.

### Render Deployment (Cloud Option)
Push your code to GitHub.

Go to Render.com and link your GitHub.

Choose "New Web Service".

Use the render.yaml provided.

Set the .env variables in the Render UI.

## How to Use
Upload legal documents (PDF, .txt, etc.).

Ask your legal question in natural language (e.g. "What are the tenant rights in this lease?").

Get a precise, referenced response from the system.

Submit feedback on responses to help improve the model.

### Configuration Guide
**File**	**What You Can Change**
prompt_templates.py:	Add/edit prompt response formats
retriever.py:	Tweak retrieval logic or scoring methods
reranker.py:	Add reranking models (e.g., Cohere)
llm.py:	Switch between OpenAI, TogetherAI, etc.
vector_store.py:	Use Pinecone or other vector DBs

### Advanced Retrieval Techniques
Query Expansion: Automatically adds synonyms/related terms to broaden recall.

Result Reranking: Sorts retrieved documents by relevance using another model.

Hybrid Search: Combines keyword + vector search (for best of both worlds).

## Customization Guide
### Add a Prompt Style
Edit the dictionary in utils/prompt_templates.py:


```python
DEFAULT_TEMPLATES["legal_summary"] = """
You are a legal assistant. Summarize the following content professionally:
{context}
"""
```

### Swap Embedding Models
Create a new class in core/embeddings.py and plug it into the pipeline.

### Use Another Vector Store
Subclass VectorStore in core/vector_store.py and define your logic (e.g., using FAISS, ChromaDB, etc.).

## Troubleshooting
Problem	Fix
ModuleNotFoundError	Activate virtualenv and run pip install -r requirements.txt
Invalid API Key	Check .env values
App won’t start	Try: streamlit run src/SmartLegalAssistant/streamlit_app/main.py
“No documents found” in UI	Upload and index docs before querying

## Contributing
We welcome contributions from learners and professionals alike!


1. Fork and clone the project
git checkout -b feature/my-feature

2. Make your changes
git commit -m "Add new feature"

3. Push and open a PR on GitHub
 - Follow PEP8
 - Write clear comments and docstrings
 - Include test cases or examples if possible

## License
This project is licensed under the MIT License.

## Feedback
We collect user feedback from the UI to help improve responses. Feedback logs are stored in:

logs/feedback/
# smart-legal-assistants using Retrieval Augmented Generation 

A scalable Retrieval-Augmented Generation application for answering questions using your document knowledge base.

## Features

- **Document Retrieval**: Efficiently retrieve relevant information from your vector database
- **Advanced RAG Pipeline**: Modular components for embeddings, retrieval, and response generation
- **Customizable Prompts**: Multiple prompt templates for different response styles
- **Query Enhancement**: Optional query expansion and result reranking
- **User-Friendly Interface**: Clean Streamlit UI with feedback collection
- **Deployment Ready**: Docker and Render configurations included


## Technologies Used

- **Python**
- **CSS**
- **Docker**

## Code Structure Overview
smart-legal-assistants/
├── .github/workflows/ # GitHub Actions workflows
├── .idea/ # JetBrains IDE configuration
│ ├── dictionaries/
│ │ └── project.xml
│ ├── inspectionProfiles/
│ │ └── profiles_settings.xml
│ ├── misc.xml
│ ├── modules.xml
│ ├── smart-legal-assistant.iml
│ └── vcs.xml
├── src/
│ └── SmartLegalAssistant/
│ ├── init.py
│ ├── core/
│ │ ├── init.py
│ │ ├── answer_generator.py
│ │ ├── embeddings.py
│ │ ├── llm.py
│ │ ├── reranker.py
│ │ ├── retriever.py
│ │ └── vector_store.py
│ ├── streamlit_app/ # Streamlit UI components
│ └── utils/
│ ├── init.py
│ ├── exception.py
│ ├── logger.py
│ └── prompt_templates.py
├── .gitignore
├── Dockerfile
├── LICENSE
├── README.md
├── experiment.ipynb
├── file.py
├── main.py
├── pyproject.toml
├── render.yaml
├── requirements.txt
├── template.py

## Setup Instructions

### Environment Variables

Create a `.env` file in the root directory with the following variables:

```
TOGETHER_API_KEY=your_together_api_key
PINECONE_API_KEY=your_pinecone_api_key
PINECONE_ENVIRONMENT=your_pinecone_environment
PINECONE_INDEX_NAME=your_pinecone_index_name
PINECONE_NAMESPACE=optional_namespace
```

### Local Installation

1. Clone the repository:
   ```
   git clone https://github.com/yourusername/rag-assistant.git
   cd rag-assistant
   ```

2. Install dependencies:
   ```
   pip install -r requirements.txt
   ```

3. Run the application:
   ```
   streamlit run app/main.py
   ```

### Docker Deployment

1. Build the Docker image:
   ```
   docker build -t rag-assistant .
   ```

2. Run the container:
   ```
   docker run -p 8501:8501 --env-file .env rag-assistant
   ```

### Render Deployment

1. Connect your GitHub repo to Render

2. Create a new Web Service

3. Use the provided render.yaml configuration

4. Set the required environment variables in the Render dashboard

### Basic Usage
Launch the app locally or via Docker/Render

Upload your document collection (PDFs, TXT, etc.)

Ask legal questions in natural language

View context-aware responses with reference sources

Submit feedback directly in the UI

### Configuration Options
You can customize behavior in the following modules:

prompt_templates.py: Add or modify response styles

retriever.py: Tune retrieval strategies and scoring

reranker.py: Apply custom reranking logic

llm.py: Switch between LLM providers (OpenAI, Together, etc.)

vector_store.py: Configure vector DB (e.g., Pinecone)

## Troubleshooting
Issue	Fix
ModuleNotFoundError	Ensure virtual environment is activated and dependencies installed
Invalid API Key	Check .env configuration
App won’t start	Run streamlit run src/SmartLegalAssistant/streamlit_app/main.py directly
No documents found	Ensure you’ve uploaded and indexed documents
## Customization

### Adding New Prompt Templates

Add your custom templates to `utils/prompt_templates.py` by extending the `DEFAULT_TEMPLATES` dictionary.

### Using Different Embedding Models

Implement a new embedding model class in `core/embeddings.py` by extending the `EmbeddingModel` base class.

### Changing Vector Stores

Implement a new vector store in `core/vector_store.py` by extending the `VectorStore` base class.

## Advanced Retrieval Techniques

- **Query Expansion**: Enhances recall by adding related terms to the query
- **Result Reranking**: Improves precision by reordering results based on relevance
- **Hybrid Search**: Combines vector and keyword-based search (configurable in settings)

## Contributing
We welcome contributions!

Fork the repo

Create a feature branch: git checkout -b feature/my-feature

Commit changes and test thoroughly

Open a Pull Request with clear context

Please follow PEP8 standards and document your code.

## License
This project is licensed under the MIT License. See the LICENSE file for details.

## Feedback and Improvement

The system collects user feedback to help improve response quality. Feedback is stored in `logs/feedback/`.
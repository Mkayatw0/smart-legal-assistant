# smart-legal-assistants using Retrieval Augmented Generation (RAG) USER

A scalable Retrieval-Augmented Generation application for answering questions using your document knowledge base.

## Features:
    - Document Retrieval: Efficiently retrieve relevant information from your vector database.
    - Advanced RAG Pipeline: Modular components for embeddings, retrieval, and response generation.
    - Customizable Prompts: Multiple prompt templates for different response styles.
    - Query Enhancement: Optional query expansion and result reranking.
    - User-Friendly Interface: Clean Streamlit UI with feedback collection.
    - Deployment Ready: Docker and Render configurations included.

## Technologies Used:
    - Python
    - CSS
    - Docker

## Code Structure:
    smart-legal-assistants/
    ├── .github/workflows/                 # GitHub Actions workflows
    ├── .idea/                             # JetBrains IDE configuration
    │   ├── dictionaries/
    │   ├── inspectionProfiles/
    ├── src/
    │   └── SmartLegalAssistant/
    │       ├── core/                      # Core components: embeddings, LLM, retriever, reranker, etc.
    │       ├── streamlit_app/             # Streamlit UI components
    │       └── utils/                     # Utilities: logger, prompts, exceptions
    ├── Dockerfile
    ├── LICENSE
    ├── README.md
    ├── render.yaml
    ├── requirements.txt
    └── main.py

## Setup:
    To run locally or deploy, configure and install the app as follows.

### Environment Variables:
    Create a `.env` file in the project root with the following:
        TOGETHER_API_KEY=your_together_api_key
        PINECONE_API_KEY=your_pinecone_api_key
        PINECONE_ENVIRONMENT=your_pinecone_environment
        PINECONE_INDEX_NAME=your_pinecone_index_name
        PINECONE_NAMESPACE=optional_namespace

### Local Installation:
    1. Clone the repository:
        git clone https://github.com/yourusername/rag-assistant.git
        cd rag-assistant
    2. Install dependencies:
        pip install -r requirements.txt
    3. Run the application:
        streamlit run app/main.py

### Docker Deployment:
    1. Build the Docker image:
        docker build -t rag-assistant .
    2. Run the container:
        docker run -p 8501:8501 --env-file .env rag-assistant

### Render Deployment:
    1. Connect your GitHub repo to Render.
    2. Create a new Web Service.
    3. Use the provided render.yaml configuration.
    4. Set the environment variables in the Render dashboard.

## Usage:
    - Launch locally or via Docker/Render.
    - Upload document collection (PDFs, TXT, etc.).
    - Ask legal questions in natural language.
    - Receive context-aware responses with source references.
    - Submit feedback through the UI.

## Configuration Options:
    Customize key behavior via the following modules:
        - utils/prompt_templates.py: Modify response prompt styles.
        - core/retriever.py: Tune retrieval strategies and scoring.
        - core/reranker.py: Customize reranking logic.
        - core/llm.py: Switch between LLM providers (e.g., OpenAI, Together).
        - core/vector_store.py: Configure vector DB (e.g., Pinecone).

## Troubleshooting:
    Common Issues and Fixes:
        - ModuleNotFoundError: Activate virtual environment and install dependencies.
        - Invalid API Key: Check your `.env` configuration.
        - App won’t start: Run `streamlit run src/SmartLegalAssistant/streamlit_app/main.py` directly.
        - No documents found: Ensure documents are uploaded and indexed.

## Customization:

    Adding New Prompt Templates:
        Add custom templates to `utils/prompt_templates.py` under `DEFAULT_TEMPLATES`.

    Using Different Embedding Models:
        Extend `EmbeddingModel` in `core/embeddings.py` to implement a new model.

    Changing Vector Stores:
        Extend `VectorStore` in `core/vector_store.py` to support a new backend.

## Advanced Retrieval Techniques:
    - Query Expansion: Improves recall by augmenting the query.
    - Result Reranking: Enhances result precision through scoring.
    - Hybrid Search: Combines vector and keyword search (toggle in config).

## Contributing:
    Contributions are welcome! To contribute:
        - Fork the repository.
        - Create a new branch: git checkout -b feature/my-feature
        - Commit and test your changes.
        - Open a Pull Request with context.

    Guidelines:
        - Follow PEP8 coding standards.
        - Add docstrings and inline documentation where appropriate.

## License:
    MIT License. See LICENSE file for full terms.

## Feedback:
    User feedback is collected to enhance system performance.
    Feedback is stored in: `logs/feedback/`           
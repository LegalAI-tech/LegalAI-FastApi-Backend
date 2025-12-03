<div align="center">

# ⚖️ Nyay Mitra: Legal AI Assistant Platform

**A comprehensive AI-powered legal assistant for Indian legal systems with intelligent document analysis, multi-language support, and advanced RAG capabilities.**

<p>
  <a href="#YOUR-LIVE-DEMO-URL"><img src="https://img.shields.io/badge/🤗-Live%20Demo%20on%20Hugging%20Face-yellow" alt="Live Demo"></a>
  <a href="/docs"><img src="https://img.shields.io/badge/API-Docs-green?logo=swagger" alt="API Docs"></a>
  <a href="https://opensource.org/licenses/Apache-2.0"><img src="https://img.shields.io/badge/License-Apache%202.0-blue.svg" alt="License: Apache 2.0"></a>
  <a href="https://fastapi.tiangolo.com/"><img src="https://img.shields.io/badge/Framework-FastAPI-05998b?logo=fastapi" alt="Framework: FastAPI"></a>
</p>
</div>

---
**Note:** This GitHub repository is for demonstration and documentation purposes. The complete, production-ready components are deployed separately:

* **AI Backend:** Hosted on Hugging Face Spaces
* **Node.js Backend:** Handles authentication and database operations
* **Frontend:** User-facing application

## ✨ Project Overview
Nyay Mitra is a full-stack legal AI assistant specifically designed for Indian legal systems. The platform combines state-of-the-art AI technologies to provide document analysis, intelligent conversational assistance, multi-language translation, and automated document generation for legal professionals and individuals seeking legal information.
**Architecture:** `Frontend Application → Node.js Backend (Auth/DB) → AI Backend (Hugging Face) → External AI Services`

## 🚀 Key Features
### Intelligent AI Agent
* **Multi-tool Reasoning Engine:** Advanced workflow automation with LangChain orchestration
* **Context-Aware Conversations:** Session management with conversation continuity
* **Automatic Language Detection:** Smart routing for 10+ languages
* **Multi-step Workflows:** Complex query handling with intelligent tool selection
### Document Processing
* **RAG-Powered Q&A:** Ask questions about uploaded documents with high accuracy
* **Duplicate Detection:** SHA-256 content hashing prevents redundant uploads
* **Adaptive Analysis:** Smart document analysis (small/medium/large strategies)
* **Hybrid Retrieval:** Semantic search with fallback mechanisms
### Multi-Language Support
* **10+ Languages:** English, Hindi, French, Urdu, Tamil, Bengali, Gujarati, Kannada, Malayalam, Telugu
* **Bridge Translation:** Direct and English-bridge translation paths
* **Automatic Detection:** Input language detection with confidence scoring
* **Context-Aware Translation:** Preserves legal terminology accuracy
### Document Generation
* **Template-Based Generation:** Jinja2 templates for legal documents
* **AI-Assisted Content:** Automated summary and content generation
* **Customizable Templates:** Support for various legal document types

## 🛠️ Technology Stack
### AI Backend (Hugging Face Spaces)
| Component | Technology | Purpose |
| :--- | :--- | :--- |
| **Framework**| FastAPI 0.111.0 | High-performance async API |
| **LLM**| Google Gemini 2.5 | AI reasoning (Flash & Pro) |
| **Orchestration**| LangChain 0.1.20 | AI workflow management |
| **RAG Engine**| LlamaIndex 0.10.34 | Document indexing & retrieval |
| **Vector Store**| ChromaDB 0.4.24 | Semantic search |
| **Embeddings**| Gemini text-embedding-004| Document vectorization |
| **Translation**| Argos Translate 1.9.0 | Self-hosted translation |
| **Storage**| Hugging Face Datasets | Document persistence |
| **Templates**| Jinja2 3.1.4 | Document generation |
### Full Stack
| Layer | Technology |
| :--- | :--- |
| **Frontend** | NextJS |
| **API Gateway**| Node.js Backend |
| **AI Processing**| FastAPI on Hugging Face |
| **Database** | NeonDB |
| **Authentication**| JWT + OAuth 2.0 |

## 📋 System Architecture
```
┌─────────────────────────────────────────────────┐
│         Frontend Application (React/Vue)        │
│  • User Interface                               │
│  • Document Upload                              │
│  • Chat Interface                               │
└──────────────────┬──────────────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────────────┐
│         Node.js Backend (Auth/Database)         │
│  • User Authentication                          │
│  • Session Management                           │
│  • Database Operations                          │
│  • Request Routing                              │
└──────────────────┬──────────────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────────────┐
│      AI Backend (Hugging Face Spaces)           │
│  ┌────────────────────────────────────────────┐ │
│  │    Nyay Mitra AI Agent (Multi-tool)        │ │
│  └────────────────────────────────────────────┘ │
│  • RAG Service (LlamaIndex + ChromaDB)          │
│  • Translation Service (Argos Translate)        │
│  • Document Generation (Jinja2)                 │
│  • Deduplication Service (SHA-256)              │
└──────────────────┬──────────────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────────────┐
│        External AI Services & Storage           │
│  • Google Gemini API (LLM & Embeddings)         │
│  • Hugging Face Hub (Document Storage)          │
└─────────────────────────────────────────────────┘
```

## ⚙️ How It Works
### Document Upload & Analysis Flow
1.  **Upload**: A user uploads a document through the frontend.
2.  **Authentication & Routing**: The Node.js backend authenticates the user and securely forwards the request to the AI backend.
3.  **Deduplication**: The AI backend checks for duplicates using **SHA-256 hashing** to prevent redundant processing.
4.  **Processing Pipeline**: If unique, the document is classified, chunked (800 characters with 150 overlap), embedded, and indexed in the **ChromaDB** vector store.
5.  **Response**: An adaptive analysis is generated based on the document's size, and the results are returned to the user.

### Conversational Query Flow
1.  **Query & Language Detection**: A user sends a query, and the system automatically identifies the input language.
2.  **Workflow Planning**: The AI Agent plans a multi-step workflow, selecting the appropriate tools (RAG, translation, etc.) for the task.
3.  **Reasoning & Execution**: The agent executes the plan, manages conversational context, and generates a coherent response.
4.  **Display**: The final response, translated if necessary, is displayed on the frontend with sources cited for transparency.

### RAG Query Processing
1.  **Retrieval**: The system performs a **semantic search** in the vector store to retrieve the top-k relevant chunks (max 12).
2.  **Context Formulation**: A context is prepared for the LLM, managing a token limit of ~8,000.
3.  **Generation**: The **Gemini (Flash/Pro)** model generates a precise answer based on the provided context and sources.

## 📊 Performance Specifications
* **Chunk Size**: 800 characters with 150 character overlap
* **Max Chunks per Query**: 12 (adaptive based on document size)
* **Context Token Limit**: 8,000 tokens (~32,000 characters)
* **Analysis Token Limit**: 20,000 tokens (~80,000 characters)
* **Similarity Threshold**: 0.3 for semantic search
* **Deduplication**: SHA-256 content hashing with in-memory cache
* **Supported Document Types**: PDF, TXT, DOCX

## 🌐 Live Deployments
### AI Backend
* **Live Demo**: [Hugging Face Space](https://huggingface.co/spaces/aryan195a/Legal-ai-backend-1)
* **API Docs**: [Interactive Swagger UI](https://aryan195a-legal-ai-backend-1.hf.space/docs#/)
* **Source Code**: [Hugging Face Repository](https://huggingface.co/spaces/aryan195a/Legal-ai-backend-1/tree/main)
### Frontend Application
* **Live Application**: [Link to Frontend](#)
* **Repository**: [Link to Frontend Repo](https://github.com/LegalAI-tech/LegalAI)
### Node.js Backend
* **API Server**: [Link to Backend](#)
* **Repository**: [Link to Backend Repo](https://github.com/LegalAI-tech/LegalAI_Backend)

<details>
<summary>🔧 View Full API Endpoints</summary>

### Primary Agent Interface
* `POST /api/v1/agent/chat` - Intelligent conversational interface
* `POST /api/v1/agent/upload-and-chat` - Upload & instant analysis
* `GET /api/v1/agent/capabilities` - System capabilities

### Document Operations
* `POST /api/v1/chat/rag` - Document Q&A
* `POST /api/v1/chat/rag/batch` - Batch questions
* `POST /document/suggest` - AI analysis & suggestions

### Translation
* `POST /api/v1/translate` - Text translation
* `POST /api/v1/agent/detect-language` - Language detection
* `GET /api/v1/agent/languages` - Supported languages

### Deduplication
* `POST /api/v1/agent/deduplication/check` - Check for duplicates
* `GET /api/v1/agent/deduplication/stats` - Deduplication statistics

### System
* `GET /health` - Health check
* `GET /` - System overview

**Full API Documentation:** [Swagger UI](https://aryan195a-legal-ai-backend-1.hf.space/docs#/)
</details>

## ⚠️ Legal Disclaimer
This AI system is for informational and educational purposes only.
* ❌ Does NOT provide legal advice
* ❌ Does NOT replace qualified legal professionals
* ❌ Does NOT guarantee accuracy or completeness
* ✅ Provides general information and analysis
* ✅ Helps organize legal information
* ✅ Should be verified by legal experts

Always consult a qualified legal professional for specific legal matters.

## 📄 License
This project is licensed under the Apache 2.0 License - see the `LICENSE` file for details.

## 👨‍💻 Built By
Tejasvi Aryan && Anubrata Guin

## 📞 Contact & Support
For questions, issues, or collaboration:
* **Email**: `tejasviaryan225@gmail.com`

## 🙏 Acknowledgments
* Google Gemini for powerful LLM capabilities
* LangChain & LlamaIndex for AI orchestration
* Hugging Face for hosting infrastructure
* Argos Translate for open-source translation
* FastAPI for excellent async framework

<div align="center">
⭐ Star this repository if you find it useful!
</div>

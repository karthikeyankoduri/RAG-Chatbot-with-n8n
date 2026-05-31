AI-Powered RAG Chatbot with n8n, Pinecone, Groq & Google Drive

<img width="1530" height="637" alt="image" src="https://github.com/user-attachments/assets/1b93338d-9074-4595-8b88-91208017919e" />


An end-to-end Retrieval-Augmented Generation (RAG) workflow built with n8n that automatically ingests documents from Google Drive, stores embeddings in Pinecone, and enables users to chat with an AI assistant that answers questions using the uploaded knowledge base.

Overview

This workflow creates a document-aware AI assistant by combining:

Google Drive for document storage
OpenAI Embeddings for vector generation
Pinecone for vector storage and retrieval
Groq (Llama 3.3 70B) for fast AI responses
n8n AI Agent for orchestration and tool usage

When a new document is added to a Google Drive folder, the workflow automatically:

Downloads the file
Extracts and chunks the content
Generates embeddings
Stores vectors in Pinecone

Users can then chat with the AI assistant, which retrieves relevant context from Pinecone before generating answers.

Problem Solved

Traditional chatbots rely only on model knowledge and cannot answer questions about custom documents.

This workflow solves that problem by:

Creating a searchable knowledge base from uploaded documents
Grounding responses in real document content
Reducing hallucinations
Allowing knowledge updates without retraining models
Architecture
Google Drive Folder
        │
        ▼
Google Drive Trigger
        │
        ▼
Download Document
        │
        ▼
Document Loader
        │
        ▼
Text Splitter
        │
        ▼
OpenAI Embeddings
        │
        ▼
Pinecone Vector Store
        │
        ▼

User Chat Query
        │
        ▼
n8n Chat Trigger
        │
        ▼
AI Agent (Groq Llama 3.3 70B)
        │
        ▼
Pinecone Retrieval Tool
        │
        ▼
Context-Aware Response
Features
Automated Document Ingestion
Monitors a specific Google Drive folder
Automatically processes newly uploaded files
No manual indexing required
Vector Database Integration
Stores document embeddings in Pinecone
Supports semantic search
Fast retrieval of relevant content
AI Agent
Powered by Groq's Llama 3.3 70B model
Uses retrieved document context before answering
Provides more accurate and relevant responses
Scalable RAG Pipeline
Chunking using Recursive Character Text Splitter
Embedding generation with OpenAI
Namespace support for organizing knowledge bases
Tech Stack
Component	Technology
Workflow Automation	n8n
LLM	Groq Llama 3.3 70B
Embeddings	OpenAI Embeddings
Vector Database	Pinecone
Storage	Google Drive
Retrieval Framework	n8n LangChain Nodes
Workflow Components
Knowledge Base Pipeline
Google Drive Trigger

Detects newly uploaded files inside the monitored folder.

Download File

Downloads the document from Google Drive.

Document Loader

Extracts text from the uploaded document.

Recursive Character Text Splitter

Splits large documents into smaller chunks for embedding.

OpenAI Embeddings

Converts document chunks into vectors.

Pinecone Vector Store

Stores embeddings in the Pinecone namespace.

Chat & Retrieval Pipeline
Chat Trigger

Receives user messages.

AI Agent

Acts as the conversational layer.

Groq Chat Model

Uses Llama 3.3 70B for response generation.

Pinecone Retrieval Tool

Retrieves relevant document chunks from the vector database.

Response Generation

Combines retrieved context with user queries to produce grounded answers.

Example Use Cases
Internal knowledge assistants
Company documentation search
Research assistants
Educational chatbots
Support knowledge bases
Policy and compliance assistants
Mental health resource assistants
Training document Q&A systems
Setup Requirements
Accounts Required
n8n
Google Drive
OpenAI API
Pinecone
Groq
Credentials Needed
Google Drive OAuth2
OpenAI API Key
Pinecone API Key
Groq API Key
How It Works
Step 1: Upload a Document

Upload a PDF or supported document into the configured Google Drive folder.

Step 2: Automatic Processing

The workflow:

Downloads the file
Splits content into chunks
Creates embeddings
Stores vectors in Pinecone
Step 3: Ask Questions

Users interact with the chat interface.

Example:

Question:

What are the key recovery strategies discussed in the document?

Process:

Query is embedded
Relevant chunks are retrieved from Pinecone
Groq generates an answer using retrieved context
Step 4: Receive Grounded Answers

Responses are based on document content rather than model memory alone.

Key Benefits
Automated document indexing
Near real-time knowledge base updates
Reduced hallucinations
Fast retrieval with Pinecone
Low-latency responses using Groq
No model fine-tuning required
Future Improvements
Multi-document support
Metadata filtering
Hybrid search
User authentication
Conversation memory
Source citation links
Multi-tenant knowledge bases
Support for DOCX, CSV, and web pages
Author

Sai Karthikeyan Koduri

AI Automation | Agentic AI | Workflow Engineering | RAG Systems | n8n Automation

GitHub: https://github.com/karthikeyankoduri

License

MIT License - Feel free to use, modify, and extend this workflow for your own RAG applications.

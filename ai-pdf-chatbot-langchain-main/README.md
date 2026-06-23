# AI PDF Chatbot & Agent Powered by LangChain and LangGr

## Features

- **Document Ingestion Graph**: Upload and parse PDFs into `Document` objects, then store vector embeddings into a vector database (we use Supabase in this example).
- **Retrieval Graph**: Handle user questions, decide whether to retrieve documents or give a direct answer, then generate concise responses with references to the retrieved documents.
- **Streaming Responses**: Real-time streaming of partial responses from the server to the client UI.
- **LangGraph Integration**: Built using LangGraph’s state machine approach to orchestrate ingestion and retrieval, visualise your agentic workflow, and debug each step of the graph.  
- **Next.js Frontend**: Allows file uploads, real-time chat, and easy extension with React components and Tailwind.

---

## Architecture Overview

```ascii
┌─────────────────────┐    1. Upload PDFs    ┌───────────────────────────┐
│Frontend (Next.js)   │ ────────────────────> │Backend (LangGraph)       │
│ - React UI w/ chat  │                      │ - Ingestion Graph         │
│ - Upload .pdf files │ <────────────────────┤   + Vector embedding via  │
└─────────────────────┘    2. Confirmation   │     SupabaseVectorStore   │
(storing embeddings in DB)

┌─────────────────────┐    3. Ask questions  ┌───────────────────────────┐
│Frontend (Next.js)   │ ────────────────────> │Backend (LangGraph)       │
│ - Chat + SSE stream │                      │ - Retrieval Graph         │
│ - Display sources   │ <────────────────────┤   + Chat model (OpenAI)   │
└─────────────────────┘ 4. Streamed answers  └───────────────────────────┘

```

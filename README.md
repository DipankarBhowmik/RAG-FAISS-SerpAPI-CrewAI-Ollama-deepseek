# SmartRAG Crew: A Zero-Cost, Local RAG System Using CrewAI and Ollama (Deepseek)
<img src="Agentic_rag.png" alt="Agentic_rag" width="400"/>
A zero-cost RAG system employing an embedded model, all-MiniLM-L6-v2, stored in an FAISS index, a fallback mechanism handled by SerpAPI's web search, powered by CrewAI and Ollama with model deepseek-r1:1.5b, and running fully on your machine.

#🚀 Features
## 🧾 Parses PDFs and extracts raw text

## 🔍 Builds a FAISS index for semantic document search

## 🧠 Uses a lightweight local model (deepseek-r1:1.5b) via Ollama

## 🌐 Falls back to web search using SerpAPI if local context is insufficient

## 🛠️ Agent-based design with the CrewAI framework

SmartRAG Crew - a Retrieval-Augmented Generation (RAG) system powered by CrewAI and Ollama, running entirely on your machine with no external API calls (unless absolutely necessary).
This project through the architecture, code, and philosophy behind SmartRAG Crew - a system that answers questions using local documents first and only falls back to web search when needed. So we will build a Retrieval-Augmented Generation (RAG) system enhanced with
PDF parsing,
Vector search via FAISS,
LLM reasoning via Ollama,
and intelligent agent workflows using the CrewAI framework.

The pipeline starts with a PDF ingestion phase (using requests + PyPDF2) where documents are downloaded, split into chunks with CharacterTextSplitter, and indexed in FAISS using HuggingFaceEmbeddings. When a query arrives, a RAG Synthesizer Agent (configured with Ollama's DeepSeek-R1 LLM) processes it by first attempting local retrieval via the FAISS retriever; if results are sparse (<200 chars), it automatically falls back to SerpAPI web search. The context is then passed to a dynamically created Task that instructs the Agent to generate a 3-paragraph answer. The Crew orchestrates this end-to-end flow - managing the Agent's execution, evaluating the Task's completion, and returning a verified response. All components interact through LangChain's document abstraction, with the Agent handling both retrieval logic (via tools) and synthesis (via LLM prompts), while the Crew ensures fault tolerance between local and web knowledge sources. Upon execution via crew.kickoff(), the system generates a contextually rich, accurate response to the user's query by combining document retrieval, reasoning, and generation in a modular, agentic framework.
<img src="flow_chart_visual selection.png" alt="Agentic_rag" width="400"/>

# 📚 Credits
## Ollama

## CrewAI

## FAISS

## SerpAPI


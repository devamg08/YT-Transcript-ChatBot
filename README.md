YouTube Transcript Chatbot (RAG-Powered AI)

A conversational AI chatbot that summarizes YouTube videos and answers user questions using Retrieval-Augmented Generation (RAG) powered by LangChain, FAISS, Google Gemini, and HuggingFace embeddings.


🚀 Project Overview

This project allows users to input a YouTube video URL and interact with it like a chatbot — asking questions or requesting summaries about the video content without watching it.

It works by extracting the video transcript, converting it into semantic embeddings, storing them in a vector database (FAISS), and retrieving the most relevant sections when the user asks a question.
Those retrieved sections are passed to Google Gemini for accurate, context-aware answers.

🧩 Tech Stack
Frontend/UI:	Streamlit	(Interactive web interface)
Backend Framework:	Python, LangChain	RAG orchestration
LLM:	Google Gemini 2.5 Flash	for contextual answer generation
Embeddings:	HuggingFace (Sentence Transformer (all-MiniLM-L6-v2)	Text → vector conversion)
Vector Database:	FAISS for	Fast semantic retrieval
Data Source:	YouTube Transcript API which fetches video transcripts
Environment Management:	python-dotenv	Secure API key loading



yt-transcript-chatbot/
│
├── app.py                      # Streamlit main app (UI + control flow)
│
├── backend/
│   ├── transcript_gen.py        # Transcript extraction & cleaning
│   ├── database.py              # Chunking, embeddings, FAISS vectorstore
│   └── agent.py                 # QA chain (retriever + Gemini + prompt)
│
├── requirements.txt             # Python dependencies
├── .env                         # API key configuration
└── README.md                    # Project documentation


🧮 Workflow Explanation

User enters YouTube URL in the Streamlit UI.

The app uses the YouTube Transcript API to fetch and clean the video’s transcript.

The transcript is split into smaller chunks (1000 characters, 200 overlap).

Each chunk is converted into a 384-dimensional embedding using HuggingFace MiniLM.

Embeddings are stored in FAISS for fast similarity search.

LangChain creates a retriever and connects it to the Gemini LLM using a prompt template.

When the user asks a question:

The query is embedded

FAISS retrieves relevant chunks

Gemini generates an accurate answer using that context

Streamlit displays the answer conversationally.

📈 Key Features

🔹 Fetches and cleans YouTube transcripts automatically

🔹 Generates embeddings for semantic understanding

🔹 Uses FAISS for fast vector similarity search

🔹 Employs LangChain to orchestrate RAG pipeline

🔹 Integrates Gemini LLM for accurate contextual Q&A

🔹 Provides clean and interactive Streamlit interface

🔹 Lightweight — runs entirely on CPU (no GPU needed)

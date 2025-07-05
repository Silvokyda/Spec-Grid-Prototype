# 📁 Project: Transcript → Embedding → Spec Grid (Browser Extension + Azure)

## 🧠 Overview
A proof-of-concept pipeline that:
1. Uses a Chrome Extension to capture live meeting transcripts (Google Meet / Zoom)
2. Splits the transcript into chunks in real-time
3. Sends each chunk to OpenAI's embedding API
4. Stores the vector + metadata into Cosmos DB
5. (Optional) Ranks relevant chunks based on a search query
6. Builds a basic "spec grid" of extracted values

---

## 🛠️ Stack
- **Chrome Extension** – captures captions from meeting platforms
- **Azure Functions** – for chunking, embedding, storing, and retrieving
- **Azure Cosmos DB** – to store chunk metadata and embeddings
- **Azure Blob Storage** – (optional) store full call logs
- **OpenAI API** – for semantic embeddings
- **Python + JS**

---

## 🧪 Setup Instructions

### 1. Clone the repo
```bash
git clone https://github.com/silvokyda/spec-grid-poc.git
cd spec-grid-poc
```

### 2. Set up Chrome Extension
- Navigate to `/extension`
- Load the folder as an unpacked extension in Chrome (chrome://extensions)
- Join a meeting → Extension auto-starts → Captions are captured

### 3. Backend Setup
#### Create virtual environment & install dependencies
```bash
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate
pip install -r requirements.txt
```

### 4. Environment Variables (.env)
```env
OPENAI_API_KEY=your_openai_key
COSMOS_DB_URL=https://your-db.documents.azure.com:443/
COSMOS_DB_KEY=your_cosmos_key
COSMOS_DB_NAME=Flowlinker
COSMOS_CONTAINER_NAME=Chunks
AZURE_STORAGE_CONNECTION_STRING=your_blob_connection_string
```

### 5. Run Azure Functions Locally
```bash
func start
```

---

## 🧩 Key Components
- `/extension/` – Chrome extension for transcript capture
- `/functions/` – Azure Functions for processing and embedding
- `/services/` – utilities for chunking, storing, embedding

---

## 📦 Folder Structure
```txt
.
├── extension
│   ├── manifest.json
│   ├── content.js
│   └── background.js
├── functions
│   ├── ingest_transcript.py
│   ├── embed_chunks.py
│   └── search_specs.py
├── services
│   ├── openai_client.py
│   ├── cosmos_client.py
│   └── chunker.py
├── .env
├── requirements.txt
└── README.md
```

---

## 🔚 Future Enhancements
- Add real-time caption support with Whisper API
- Automatically connect to Slack/email content
- Add UI to preview and export the spec grid
- Deploy everything to Azure cloud

---

## 📬 Contact
Built by [Silvanus Owino](https://github.com/silvokyda)

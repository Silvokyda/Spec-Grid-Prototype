# 📁 Project: Transcript → Embedding → Spec Grid (Azure + OpenAI)

## 🧠 Overview
A simple proof-of-concept pipeline that:
1. Accepts a transcript (text file or JSON)
2. Splits it into chunks
3. Sends each chunk to OpenAI's embedding API
4. Stores the vector + metadata into Cosmos DB
5. (Optional) Ranks relevant chunks based on a search query
6. Builds a basic "spec grid" of extracted values

---

## 🛠️ Stack
- **Azure Functions** – for chunking, embedding, storing, and retrieving
- **Azure Cosmos DB** – to store chunk metadata and embeddings
- **Azure Blob Storage** – to store original transcript files
- **OpenAI API** – for semantic embeddings
- **Python 3.10+**

---

## 🧪 Setup Instructions

### 1. Clone the repo
```bash
git clone https://github.com/silvokyda/spec-grid-poc.git
cd spec-grid-poc
```

### 2. Create virtual environment & install dependencies
```bash
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows
pip install -r requirements.txt
```

### 3. Environment Variables (.env)
Create a `.env` file:
```env
OPENAI_API_KEY=your_openai_key
COSMOS_DB_URL=https://your-db.documents.azure.com:443/
COSMOS_DB_KEY=your_cosmos_key
COSMOS_DB_NAME=Flowlinker
COSMOS_CONTAINER_NAME=Chunks
AZURE_STORAGE_CONNECTION_STRING=your_blob_connection_string
```

### 4. Run Local Azure Functions
```bash
func start  # After installing Azure Functions Core Tools
```

---

## 🧩 Key Functions
- `/ingest-transcript` – accepts transcript text, chunks it
- `/embed-chunks` – sends to OpenAI and stores embeddings
- `/search-specs` – accepts a prompt and returns best-matching chunks

---

## 📦 Folder Structure
```txt
.
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
- Add summary generation with GPT-4
- Add Slack/email scraping prototype
- Deploy to Azure
- Write blog post with live demo

---

## 📬 Contact
Built by [Silvanus Owino](https://github.com/silvokyda)

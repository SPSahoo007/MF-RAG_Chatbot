# Mutual Fund AI Assistant (RAG Pipeline) 🚀

A real-time Retrieval-Augmented Generation (RAG) chatbot designed to accurately answer mutual fund queries based strictly on scraped data from verified sources (like AMFI and Groww).

This project features a modern, minimalist glassmorphism UI and a robust Flask backend that processes queries against a local ChromaDB vector database.

## 🌟 Features
- **Facts-Only Guardrails**: The LLM refuses to provide speculative investment advice or performance predictions.
- **Automated Data Pipeline**: A GitHub Actions workflow runs every day at 10:30 IST to scrape the latest NAVs and Expense Ratios, update the vector database, and commit the fresh data.
- **Hugging Face Spaces Optimized**: Fully containerized with a Dockerfile for seamless, free deployment on Hugging Face Spaces (16GB RAM).
- **Multi-Chat UI**: Dynamic local storage chat history and conversation threading.

## 🛠️ Architecture

1. **Scraper (`src/scraper.py`)**: Fetches live mutual fund scheme pages.
2. **Chunker (`src/chunking.py`)**: Parses the raw HTML to Markdown, extracting key financial metrics (Expense Ratio, NAV, AUM) into high-priority metadata chunks.
3. **Embedder (`src/embed_and_store.py`)**: Uses Langchain and HuggingFace BGE Embeddings to convert text into vectors stored in ChromaDB.
4. **Backend (`app.py`)**: A Flask API that queries the ChromaDB and routes the context to a Groq LLM (Llama 3).
5. **Frontend (`templates/index.html`)**: A beautiful, vanilla JS & Tailwind CSS interface.

## 🚀 Setup & Local Deployment

### Prerequisites
- Python 3.9+
- A [Groq API Key](https://console.groq.com/keys)

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/SPSahoo007/MF-RAG_Chatbot.git
   cd MF-RAG_Chatbot
   ```
2. Create and activate a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate
   ```
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Set up environment variables:
   Copy `.env.example` to `.env` and insert your API key:
   ```env
   GROQ_API_KEY=gsk_your_key_here
   ```

### Running the App
Start the Flask server:
```bash
python app.py
```
Then navigate to `http://127.0.0.1:7860` in your browser.

## ☁️ Cloud Deployment (Hugging Face Spaces)
Because the Machine Learning libraries (`sentence-transformers`, `torch`) exceed standard serverless limits (like Vercel's 250MB limit), this app is heavily optimized for **Hugging Face Spaces**.
1. Create a new Space on [Hugging Face](https://huggingface.co/).
2. Select **Docker** as the SDK.
3. Link this GitHub repository.
4. Add your `GROQ_API_KEY` to the Space Secrets.
5. Hugging Face will automatically build and deploy the container!
## ⚠️ Disclaimer
This tool is for educational purposes only. It is strictly built to demonstrate Retrieval-Augmented Generation (RAG) techniques and does not constitute financial advice. Always consult a registered financial advisor before making investment decisions.

## 📄 License
This project is licensed under the MIT License.

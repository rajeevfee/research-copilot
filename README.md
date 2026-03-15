# 🔬 ResearchCopilot — AI-Powered Research Assistant

A complete, fully-functional AI research assistant that runs as a **single HTML file**. No backend required. Host on GitHub Pages and share via direct URL.

**[▶ Live Demo](https://your-username.github.io/research-copilot)** ← Replace with your GitHub Pages URL

---

## ✨ Features

| Module | Description |
|--------|-------------|
| 📤 **Upload Documents** | Add PDFs, TXT, MD files or paste text directly |
| 🗄 **Knowledge Base** | Semantic search, topic clustering, chunk viewer |
| 💬 **Research Chat** | Multi-turn RAG-powered Q&A with citations |
| 📋 **Literature Review** | Auto-generate structured reviews from your corpus |
| 🔍 **Research Gaps** | Identify unexplored directions and limitations |
| 💡 **Idea Generator** | Novel research ideas grounded in your papers |
| 🧪 **Experiment Designer** | Full ML pipeline design with specifics |
| ⚙ **Code Generator** | Clean PyTorch/TF/sklearn code from natural language |
| ✍ **Paper Writer** | Publication-ready section drafts |

---

## 🚀 Quick Start (5 minutes)

### Option 1: GitHub Pages (Recommended — Free, instant)

1. **Fork or clone this repo**
   ```bash
   git clone https://github.com/YOUR_USERNAME/research-copilot.git
   cd research-copilot
   ```

2. **Push to GitHub**
   ```bash
   git add .
   git commit -m "Initial deploy"
   git push origin main
   ```

3. **Enable GitHub Pages**
   - Go to your repo → `Settings` → `Pages`
   - Source: `Deploy from a branch`
   - Branch: `main` / `/ (root)`
   - Click Save

4. **Access your site**
   - URL: `https://YOUR_USERNAME.github.io/research-copilot`
   - Available in ~2 minutes

5. **Get an Anthropic API Key**
   - Visit [console.anthropic.com](https://console.anthropic.com)
   - Create account → API Keys → Create key
   - Paste your key into the app's setup screen

---

### Option 2: Local Development

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/research-copilot.git
cd research-copilot

# Serve locally (any of these work)
python3 -m http.server 8000
# OR
npx serve .
# OR just open index.html in Chrome/Firefox
```

Open `http://localhost:8000` and enter your API key.

---

### Option 3: One-Click Deploy

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/YOUR_USERNAME/research-copilot)

[![Deploy to Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/YOUR_USERNAME/research-copilot)

---

## 🔑 API Key Security

Your Anthropic API key is:
- ✅ Stored **only in your browser's localStorage**
- ✅ Sent **only to Anthropic's API directly** from your browser
- ✅ **Never touches any intermediate server**
- ✅ Cleared when you click "Clear All Data" in Settings

> **Important:** This is a public GitHub Pages site. Anyone with the URL can use it — but they need their **own API key**. Your key is never exposed.

---

## 🏗 Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    Browser (Client-side)                 │
│                                                         │
│  ┌──────────────┐   ┌──────────────┐   ┌────────────┐  │
│  │  Document    │   │   Client     │   │  Claude    │  │
│  │  Ingestion   │──▶│   RAG        │──▶│  API       │  │
│  │              │   │  Pipeline    │   │  claude-   │  │
│  │ - Text parse │   │              │   │  sonnet-4  │  │
│  │ - Chunking   │   │ - BM25 retrieval│  │            │  │
│  │ - Topic      │   │ - Context    │   │  Grounded  │  │
│  │   detection  │   │   building   │   │  Answers   │  │
│  └──────────────┘   └──────────────┘   └────────────┘  │
│           │                                             │
│           ▼                                             │
│  ┌──────────────────────────────────┐                  │
│  │       localStorage               │                  │
│  │  - Documents + chunks            │                  │
│  │  - API key                       │                  │
│  │  - Chat history                  │                  │
│  └──────────────────────────────────┘                  │
└─────────────────────────────────────────────────────────┘
```

### RAG Pipeline (Client-Side)

1. **Ingest** → Extract text, clean whitespace, detect encoding
2. **Chunk** → Split into 800-token overlapping chunks (100 token overlap)
3. **Index** → Store chunks in localStorage with metadata
4. **Retrieve** → BM25-style keyword scoring across all chunks
5. **Generate** → Top-5 chunks + query sent to Claude API
6. **Cite** → Claude returns grounded answers with `[Source, §Section]` citations

---

## 📁 File Structure

```
research-copilot/
├── index.html          # Complete app (single file, ~1500 lines)
├── README.md           # This file
├── .github/
│   └── workflows/
│       └── deploy.yml  # Optional: auto-deploy workflow
└── CNAME               # Optional: custom domain
```

---

## ⚙ Configuration

All configuration is done in the app's **Settings** page:

| Setting | Description |
|---------|-------------|
| API Key | Your Anthropic API key |
| Model | claude-sonnet-4 (default), claude-opus-4, claude-haiku-4.5 |
| Export KB | Download your knowledge base as JSON |
| Import KB | Restore from exported JSON |
| Clear All | Reset all data |

---

## 📄 Supported File Formats

| Format | Support |
|--------|---------|
| `.txt` | ✅ Full text extraction |
| `.md` | ✅ Full text extraction |
| `.csv` | ✅ Full text extraction |
| `.pdf` | ⚠ Limited (binary) — **paste text for best results** |
| `.docx` | ⚠ Limited — **paste text for best results** |
| Paste text | ✅ Best option for all papers |

> **PDF Tip:** For PDF papers, the best workflow is: open the PDF → Select All → Copy → Paste into the "Paste Text" box in Upload Documents.

---

## 💰 Cost Estimate (Anthropic API)

| Action | Tokens Used | ~Cost |
|--------|-------------|-------|
| Research Chat (per message) | ~2,000 | ~$0.003 |
| Literature Review (full) | ~3,000 | ~$0.005 |
| Code Generation | ~2,500 | ~$0.004 |
| Paper Section | ~2,000 | ~$0.003 |
| Experiment Design | ~2,500 | ~$0.004 |

*Prices based on claude-sonnet-4 at $3/$15 per million input/output tokens. Actual usage varies.*

---

## 🔄 GitHub Pages Auto-Deploy

The app auto-deploys whenever you push to `main`. To set up:

```yaml
# .github/workflows/deploy.yml
name: Deploy to GitHub Pages
on:
  push:
    branches: [main]
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/configure-pages@v3
      - uses: actions/upload-pages-artifact@v2
        with:
          path: '.'
      - uses: actions/deploy-pages@v2
```

---

## 🛡 Privacy & Data

- **No analytics** — no tracking, no telemetry
- **No server** — pure static site
- **No accounts** — API key only
- **Local storage** — all data in YOUR browser
- **Open source** — audit the code yourself

---

## 🤝 Contributing

1. Fork the repository
2. Make your changes to `index.html`
3. Test locally with `python3 -m http.server 8000`
4. Submit a pull request

---

## 📜 License

MIT License — free for personal and commercial use.

---

## 🙏 Credits

Built with [Claude AI](https://anthropic.com) by Anthropic.

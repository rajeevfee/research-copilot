# 🔬 ResearchCopilot — Free AI Research Assistant

> No API key. No cost. No sign-up. Powered by Claude AI via Puter.js.

## ⚡ One-Click Deploy to Netlify

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/rajeevfee/research-copilot)

**Click → Connect GitHub → Done. Live in 60 seconds. Zero cost forever.**



---

## 🎉 Completely Free — How?

This app uses **[Puter.js](https://puter.com)** which provides free access to Claude AI models including Claude Sonnet 4.6, Claude Opus 4.6, and Claude Haiku 4.5 — no API key, no billing, no limits.

```html
<!-- This single line gives you free Claude access -->
<script src="https://js.puter.com/v2/"></script>
```

Users pay nothing. Developers pay nothing. Just deploy and use.

---

## 🚀 Deploy in 3 Steps

**Step 1** — Fork this repo (click Fork on GitHub)

**Step 2** — Click the Deploy button above → Connect GitHub → Deploy

**Step 3** — Open your live URL → Click "Launch" → Start researching

No API key screen. No setup. Just works.

---

## ✨ Features

| Module | Description |
|--------|-------------|
| 📤 Upload Docs | Paste text or upload TXT/MD — auto-chunked for RAG |
| 🗄 Knowledge Base | Semantic search, topic clusters, chunk explorer |
| 💬 Research Chat | Multi-turn Q&A with streaming + citations |
| 📋 Literature Review | Structured reviews with method comparison |
| 🔍 Research Gaps | Identify unexplored directions |
| 💡 Idea Generator | Novel ideas grounded in your papers |
| 🧪 Experiment Designer | Full ML pipeline design |
| ⚙ Code Generator | PyTorch/TF/HuggingFace code |
| ✍ Paper Writer | Publication-ready section drafts |

---

## 🤖 Available Models (all free via Puter.js)

- `claude-sonnet-4-6` ⭐ (default, recommended)
- `claude-opus-4-6` (most capable)
- `claude-haiku-4-5` (fastest)
- `claude-sonnet-4-5`
- `claude-opus-4-5`

Switch models anytime from the sidebar.

---

## 🏗 Architecture

```
Browser → Puter.js → Claude AI → Your App
   ↑
localStorage (your docs, chat history)
No server. No backend. No database.
```

- Pure static HTML/CSS/JS — single `index.html` file
- Client-side RAG: chunking, indexing, BM25 retrieval
- localStorage for all your documents and history
- Puter.js handles all AI calls for free

---

## 📄 File Structure

```
research-copilot/
├── index.html       ← Complete app
├── netlify.toml     ← Netlify config
└── README.md        ← This file
```

---

## 🛠 Local Development

```bash
git clone https://github.com/YOUR_USERNAME/research-copilot.git
cd research-copilot
python3 -m http.server 8000
# Open http://localhost:8000
```

---

## 📜 License

MIT — free for personal and commercial use.

Built with [Claude AI](https://anthropic.com) · Free hosting via [Netlify](https://netlify.com) · Free AI via [Puter.js](https://puter.com)

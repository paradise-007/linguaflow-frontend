# 🌐 LinguaFlow — Neural Translation Frontend

> A sleek, dark-themed web app for neural machine translation across French, English, Hindi, and Gujarati. Built with vanilla HTML/CSS/JS, deployed on Vercel, powered by a FastAPI backend.

[![Vercel](https://img.shields.io/badge/Deployed_on-Vercel-000000?style=flat-square&logo=vercel&logoColor=white)](https://vercel.com)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

---

## 🔗 Part of the LinguaFlow Project

| Component | Repository | Description |
|-----------|-----------|-------------|
| 📓 **Research** | [`French-To-English-Translation-NLP`](https://github.com/paradise-007/French-To-English-Translation-NLP) | Original LSTM seq2seq research & notebook |
| ⚡ **API Backend** | [`linguaflow-api`](https://github.com/paradise-007/linguaflow-api) | FastAPI backend serving MarianMT models |
| 🌐 **This repo** | `linguaflow-frontend` | This Vercel-hosted web UI |

---

## ✨ Features

- **4 languages** — French 🇫🇷, English 🇬🇧, Hindi 🇮🇳, Gujarati 🇮🇳
- **Side-by-side panels** — input and output always visible together
- **⇄ Swap languages** — flip direction instantly, output becomes new input
- **↩ Verify** — back-translate the output to check accuracy
- **🔊 Listen** — text-to-speech in the target language
- **📋 Copy** — one-click copy of translation
- **Ctrl+Enter** — keyboard shortcut to translate
- **API status indicator** — live green/red dot in the navbar
- **Demo fallback** — common phrases work even when API is sleeping
- **Zero dependencies** — pure HTML, CSS, JavaScript, no frameworks

---

## 🖼️ Screenshots

```
┌─────────────────────────────────────────────────────┐
│  LinguaFlow          Translate  Setup  GitHub ↗     │
│                                        ● API Online │
├─────────────────────────────────────────────────────┤
│                                                      │
│           Translate Without Limits                   │
│                                                      │
│  🇫🇷 French  🇬🇧 English  🇮🇳 Hindi  🇮🇳 Gujarati    │
│                                                      │
├──────────────────────────────────────────────────────┤
│ From: [French ▼]   ⇄   To: [English ▼]              │
├──────────────────┬───────────────────────────────────┤
│ French           │ English                           │
│                  │                                   │
│ Bonjour, comment │ Hello, how are you?               │
│ allez-vous ?     │                                   │
│                  │                                   │
├──────────────────┴───────────────────────────────────┤
│ 🔊 Listen  📋 Copy  ✕ Clear  ↩ Verify    [Translate]│
└──────────────────────────────────────────────────────┘
```

---

## 🚀 Getting Started

### Option A — Use the live site

1. Visit the deployed Vercel URL
2. Click **⚙ Configure** in the top-right
3. Paste your [LinguaFlow API](https://github.com/paradise-007/linguaflow-api) URL
4. Click **Save & Test** — the dot turns green ✓

### Option B — Run locally

```bash
git clone https://github.com/paradise-007/linguaflow-frontend.git
cd linguaflow-frontend

# Just open index.html — no build step needed
open index.html      # macOS
start index.html     # Windows
```

### Deploy your own on Vercel

```bash
# Install Vercel CLI
npm install -g vercel

# Deploy
vercel --prod
```

Or connect this repo on [vercel.com](https://vercel.com) → **New Project → Import Git Repository**.

---

## 📂 Project Structure

```
linguaflow-frontend/
│
├── index.html     # Entire app — HTML + CSS + JS in one file
├── vercel.json    # Vercel routing config
└── README.md
```

---

## ⚙️ Configuration

The app stores your API URL in `localStorage`. No environment variables needed.

**To connect your backend:**
1. Deploy [linguaflow-api](https://github.com/paradise-007/linguaflow-api) on Render
2. Open the frontend, click **⚙ Configure**
3. Paste your Render URL (e.g. `https://linguaflow-api.onrender.com`)
4. Click **Save & Test**

The URL persists in your browser — no need to re-enter on refresh.

---

## 🏗️ Architecture

```
User (Browser)
     ↓  types text, clicks Translate
index.html (Vercel)
     ↓  fetch("/translate?text=...&src=fr&tgt=en")
linguaflow-api (Render / FastAPI)
     ↓  loads Helsinki-NLP MarianMT model
     ↓  runs inference
     ↑  {"translation": "Hello", "src": "fr", "tgt": "en"}
index.html
     ↑  renders translation in output panel
```

**Why FastAPI and not Streamlit?**

Streamlit blocks iframe embedding (`X-Frame-Options: SAMEORIGIN`) and doesn't send CORS headers, making it impossible to call from a browser frontend. FastAPI is a proper REST API framework that handles both correctly.

---

## 🔬 Research Background

This frontend is the production face of a larger NLP project. The translation models trace back to:

1. An [LSTM seq2seq model](https://github.com/paradise-007/French-To-English-Translation-NLP) trained from scratch on French-English parallel data (the original research)
2. Production-upgraded to [Helsinki-NLP MarianMT](https://huggingface.co/Helsinki-NLP) transformer models for accuracy and multilingual support

---

## 👤 Author

**Vishv** — [@paradise-007](https://github.com/paradise-007)

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

---

<div align="center">
  <sub>LinguaFlow · Research → API → Frontend · Built end to end by <a href="https://github.com/paradise-007">@paradise-007</a></sub>
</div>

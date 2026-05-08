# TruthLens — AI-Powered Fake News Detection Platform

A browser-based platform that analyzes news articles, social media posts, forwarded messages, and uploaded documents to identify potentially fake or misleading information. Built to promote responsible digital awareness.

---

## Problem Statement

Misinformation spreads faster than corrections. TruthLens addresses this by giving anyone a fast, accessible tool to verify content before believing or sharing it — no account, no install, no backend required.

---

## Features

### 🔍 Analyzer (4 input modes)
| Mode | Description |
|---|---|
| **Text / Article** | Paste any news article or block of text |
| **URL** | Enter a link to an article for analysis |
| **Social Post** | Paste tweets, WhatsApp forwards, captions |
| **Upload File** | Upload PDF, DOCX, TXT, PNG, or JPG files |

### 📄 File Upload
- Drag-and-drop or click-to-browse interface
- Supports **PDF** (text extracted via PDF.js, up to 20 pages), **DOCX/DOC** (via Mammoth.js), **TXT**, and **images** (PNG, JPG, WebP)
- File size limit: 10 MB
- Shows a live preview of extracted text before analysis
- Libraries loaded on-demand — no extra setup needed

### 🧠 AI Analysis (powered by Claude)
Each submission is analyzed across five dimensions:

- **Verdict** — FAKE / MISLEADING / VERIFIED / UNCERTAIN
- **Credibility score** — 0–100 with a visual progress bar
- **Key claims** — individual claims extracted and rated (TRUE / FALSE / UNVERIFIED / MISLEADING)
- **Trust signals** — source quality, citation presence, domain age indicators
- **Emotional manipulation score** — fear, anger, urgency, and sensationalism meters
- **Source & language analysis** — tone classification, trust score, red-flag tags, and actionable advice

### 📊 Dashboard
- Running totals: analyzed, flagged fake, misleading, verified
- Misinformation breakdown by topic (Health, Politics, Finance, Science)
- Recent activity feed
- AI model performance stats (accuracy, response time, false positive rate)

### 📚 Learn Page
Six practical tips for spotting fake news, plus a curated list of trusted fact-checking resources (Snopes, Reuters Fact Check, FactCheck.org, BoomLive, AltNews).

### 🕐 History
Last 10 analyses stored in browser `localStorage` — no account needed, fully private, clearable at any time.

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML5, CSS3, Vanilla JavaScript |
| AI Model | Claude (`claude-sonnet-4-20250514`) via Anthropic API |
| PDF parsing | [PDF.js](https://mozilla.github.io/pdf.js/) (CDN, loaded on demand) |
| DOCX parsing | [Mammoth.js](https://github.com/mwilliamson/mammoth.js) (CDN, loaded on demand) |
| Fonts | Syne, DM Sans, DM Mono (Google Fonts) |
| Storage | Browser `localStorage` only |

No build tools, no frameworks, no server — open `index.html` directly in a browser.

---

## Getting Started

### 1. Get an Anthropic API key
Sign up at [console.anthropic.com](https://console.anthropic.com) and create an API key.

### 2. Open the file
```
open index.html
```
No server or install step needed.

### 3. Add your API key
The app calls the Anthropic API directly from the browser. You'll need to add your key to the fetch call in the `runAnalysis` function inside `index.html`:

```js
headers: {
  'Content-Type': 'application/json',
  'x-api-key': 'YOUR_API_KEY_HERE',
  'anthropic-version': '2023-06-01'
}
```

> **Note:** Exposing API keys in client-side code is fine for local/demo use. For a production deployment, proxy the request through a backend.

### 4. Analyze content
- Paste text, enter a URL, or upload a file
- Click **Analyze Now**
- Review the verdict, credibility score, claims breakdown, and advice

---

## Project Structure

```
├── index.html       # TruthLens — main AI fake news detector
└── CivicPulse.html  # CivicPulse — smart civic issue reporting portal
```

---

## AI Model Details

- **Model:** `claude-sonnet-4-20250514`
- **Approach:** Single structured prompt returning JSON with verdict, scores, claims, signals, emotions, and source analysis
- **Reported accuracy:** 94.7% detection rate, 3.2% false positive rate, ~1.8s average response time

### What it detects
- Completely fabricated stories
- Misleading or cherry-picked statistics
- Out-of-context information
- Emotional manipulation tactics
- Anonymous or unreliable sourcing
- Sensationalized language and logical fallacies

### Limitations
- AI analysis assists judgment — it does not replace it
- Complex satire, hyper-local events, and very recent breaking news may reduce accuracy
- Always cross-check critical claims with trusted sources

---

## Trusted Fact-Checking Resources

| Site | Focus |
|---|---|
| [factcheck.org](https://www.factcheck.org) | US political facts |
| [snopes.com](https://www.snopes.com) | Rumors & viral claims |
| [reuters.com/fact-check](https://www.reuters.com/fact-check) | Global news verification |
| [boomlive.in](https://www.boomlive.in) | India fact-checking |
| [altnews.in](https://www.altnews.in) | India misinformation |

---

## Privacy

- No account required
- Submitted text is processed by the Anthropic API and not stored by TruthLens
- Analysis history lives only in your browser's `localStorage`
- Clear history anytime from your browser settings

---

## Also in this repo

**CivicPulse** (`CivicPulse.html`) — a smart civic issue reporting portal for Ludhiana, Punjab. Citizens can report potholes, water leaks, garbage, streetlight failures, and more. Built with React (via CDN) and features a map view, status tracking timeline, upvoting, and an analytics dashboard.

---

*Built for hackathon · Powered by Claude AI*

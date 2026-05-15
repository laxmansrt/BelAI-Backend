<div align="center">

# 🌾 BelAI
### *AI-Powered Agricultural Intelligence for Bharat*

<br/>

[![Live Demo](https://img.shields.io/badge/🚀_Live_Demo-bel--ai.vercel.app-22c55e?style=for-the-badge)](https://bel-ai.vercel.app)
[![Hackathon](https://img.shields.io/badge/🏆_SJCIT_Hackathon-2026-f59e0b?style=for-the-badge)](#)
[![License](https://img.shields.io/badge/License-MIT-3b82f6?style=for-the-badge)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-Welcome-ec4899?style=for-the-badge)](https://github.com/laxmansrt/sjcit-hack/pulls)

<br/>

> **Empowering 100 million+ Indian farmers with AI — even on a ₹1,500 JioPhone with no internet.**

<br/>

[🎯 Problem](#-the-problem) · [💡 Solution](#-our-solution) · [✨ Features](#-features) · [🛠️ Tech Stack](#️-tech-stack) · [🚀 Quick Start](#-quick-start)

</div>

---

## 🎯 The Problem

India has **146 million farming households**. Yet:

| Challenge | Impact |
|-----------|--------|
| 🌿 Crop diseases go undetected | **₹90,000 Cr** lost annually |
| 📉 No access to real mandi prices | Farmers earn **30–40% less** than market rate |
| 🚜 Equipment too expensive to own | Small farmers **cannot afford** machinery |
| 📵 No smartphone or internet | **65% of rural India** uses basic feature phones |
| 🗣️ Language barrier | Most AI tools support only English |

**Existing solutions fail farmers** — they're built for tech-savvy urban users, require stable internet, and don't work on feature phones.

---

## 💡 Our Solution

**BelAI** is a full-stack AI agricultural platform that works for *every* Indian farmer — whether they have a smartphone or a ₹1,500 JioPhone, whether they have 4G or EDGE, whether they speak Kannada or Tamil.

```
A farmer in rural Karnataka spots a diseased crop leaf at 6 AM.
He has a JioPhone. No smartphone. Patchy internet.

→ He opens BelAI Lite on his keypad phone (works on 2G).
→ Uploads a photo of the diseased leaf.
→ BelAI instantly identifies "Leaf Blight" with Gemini Vision AI.
→ Gets organic remedy steps in Kannada via voice.
→ Checks today's tomato price at his local mandi.
→ Books a sprayer from a neighbor's equipment listing.
→ Delivery tracked on-chain. Payment split auto-executed.

All of this. On a feature phone. In his mother tongue. In under 3 minutes.
```

---

## ✨ Features

### 🩺 Vision AI — Crop Disease Doctor
> *Upload a photo. Get a diagnosis. Save your harvest.*

- Powered by **Gemini 2.5 Flash Vision** + **Llama Vision**
- Identifies disease name, severity (Low / Medium / High), and treatment
- Suggests **organic & chemical remedies** with dosage
- Works with leaf, stem, and fruit photos

---

### 📱 Universal Lite Mode — Built for JioPhone
> *Because 65% of rural India doesn't have a smartphone.*

- **Zero JavaScript** — pure HTML, works on KaiOS & Nokia keypad phones
- Loads in **under 3 seconds on 2G**
- Full feature parity: disease detection, prices, planner — all accessible
- Separate `manifest.webapp` for KaiOS app store listing

---

### 💬 WhatsApp & Voice Bot — AI in Your Mother Tongue
> *No app download needed. Just send a WhatsApp message.*

- Powered by **Twilio Programmable Voice + WhatsApp Sandbox**
- Transcribes voice notes using **Groq Whisper**
- Responds in **Kannada, Hindi, Telugu, Tamil, English**
- Maintains **8-message conversation memory** per user session (stored in MongoDB)
- Farmer dials a number → AI picks up → conversation in local language

---

### 🚜 Equipment Marketplace — Peer-to-Peer Farm Rentals
> *Own a tractor? Rent it out. Need one? Book it in 60 seconds.*

- Farmers list equipment with photos, pricing, and availability
- **Real-time cost calculator** (hourly/daily rates)
- **30% advance** booking logic with automated payment split
- In-app booking confirmation with pickup/drop coordination

---

### 📈 Real-Time Mandi Prices — Crowdsourced & Verified
> *Know the actual local price before you sell.*

- Live crop prices from local mandis across Karnataka, Maharashtra, UP
- **Community upvoting system** — farmers confirm prices they've seen today
- Prevents price manipulation; highlights most-confirmed price per commodity
- Works offline (last-fetched prices cached via Service Worker)

---

### 🔗 Blockchain Ledger — Tamper-Proof Crop Delivery Tracking
> *Every crop movement. On record. Forever.*

- SHA-256 hashed ledger simulating tamper-proof transaction records
- Tracks every delivery from farm → truck → mandi
- **75/25 smart-contract split**: Farmer gets 75%, platform takes 25%
- Full audit trail — accessible by both farmer and buyer

---

### 📅 Smart Crop Planner — AI Knows Your Soil
> *Tell BelAI your soil, district, and season. Get 5 ideal crops.*

- Input: Soil type, District, Season, Rainfall level
- Output: Top 5 recommended crops with reasoning
- Backed by **Groq Llama-3** with agri-domain prompting
- Recommendations update seasonally

---

## 🛠️ Tech Stack

<div align="center">

| Layer | Technology | Why |
|-------|-----------|-----|
| **Frontend** | Vanilla HTML5, CSS3, JS (ES6+) | Zero-dependency, loads fast on 2G |
| **UI Design** | Glassmorphism + Responsive Grid | Modern, judge-friendly, mobile-first |
| **AI — Text** | Groq (Llama-3) | Ultra-fast inference, free tier |
| **AI — Vision** | Gemini 2.5 Flash | Best-in-class image understanding |
| **AI — Voice** | Groq Whisper | Multilingual transcription |
| **Voice/WhatsApp** | Twilio | Industry standard, production-grade |
| **Backend** | Node.js + Express.js | Fast, lightweight REST API |
| **Database** | MongoDB Atlas | Flexible schema, free M0 cluster |
| **Auth** | Google OAuth 2.0 | Trusted, one-tap login |
| **Maps** | Leaflet.js + OpenStreetMap | Free, offline-capable tile caching |
| **PWA** | Service Workers + Web App Manifest | Installable, offline-first |
| **KaiOS** | `manifest.webapp` | JioPhone app store compatible |
| **Containers** | Docker + Docker Compose | Reproducible local environment |
| **Orchestration** | Kubernetes (HPA, Ingress) | Production-scale auto-scaling |
| **Hosting** | Vercel (Frontend + Serverless) | Free, instant global CDN |

</div>

---

## 📐 Architecture

```
                        ┌─────────────────────────────────┐
                        │           FARMER                │
                        │  Smartphone / JioPhone / WhatsApp│
                        └────────────┬────────────────────┘
                                     │
              ┌──────────────────────▼──────────────────────┐
              │              BelAI Frontend                 │
              │   index.html (Full) │ lite.html (JioPhone)  │
              │   belai-features.js │ service-worker.js     │
              └──────────────────────┬──────────────────────┘
                                     │ REST API calls
              ┌──────────────────────▼──────────────────────┐
              │           Node.js + Express Backend          │
              │  /api/chat  /api/diagnose  /api/prices       │
              │  /api/equipment  /api/planner  /api/ledger   │
              │  /webhook/twilio  /webhook/whatsapp          │
              └───────┬──────────────┬───────────┬──────────┘
                      │              │           │
         ┌────────────▼──┐  ┌────────▼──┐  ┌────▼──────────┐
         │  MongoDB Atlas │  │ Groq API  │  │  Gemini API   │
         │  (Chat Memory) │  │ Llama-3   │  │  Vision Model │
         │  (Marketplace) │  │ Whisper   │  │               │
         └────────────────┘  └───────────┘  └───────────────┘
                                     │
                        ┌────────────▼────────────┐
                        │     Twilio Platform      │
                        │  WhatsApp Sandbox        │
                        │  Programmable Voice      │
                        └─────────────────────────┘
```

---

## 🚀 Quick Start

### Prerequisites
- Node.js v18+
- MongoDB Atlas account (free M0 cluster)
- API Keys: Groq, Gemini, Twilio, Google OAuth

### 1️⃣ Clone
```bash
git clone https://github.com/laxmansrt/sjcit-hack.git
cd sjcit-hack
```

### 2️⃣ Backend
```bash
cd backend
npm install
cp .env.example .env   # Fill in your API keys
npm run dev            # Starts on http://localhost:4000
```

### 3️⃣ Frontend
```bash
cd ../frontend
npx serve .            # Starts on http://localhost:3000
```

### 🐳 Or run everything with Docker
```bash
docker-compose up --build
# Frontend → http://localhost:80
# Backend  → http://localhost:4000
```

### Environment Variables
```env
MONGODB_URI=mongodb+srv://...
GROQ_API_KEY=gsk_...
GEMINI_API_KEY=AIza...
TWILIO_ACCOUNT_SID=AC...
TWILIO_AUTH_TOKEN=...
TWILIO_PHONE_NUMBER=+1...
GOOGLE_CLIENT_ID=....apps.googleusercontent.com
```

---

## 🧠 Design Decisions

**Why Vanilla JS and not React?**
React adds ~130KB to the bundle. On a 2G JioPhone connection at 64Kbps, that's 17 seconds just to load the framework. Vanilla JS keeps the full app under 50KB — it loads in under 3 seconds even on EDGE.

**Why Groq instead of OpenAI?**
Groq's LPU inference is 10–25x faster than GPT-4. For a voice bot conversation, response latency matters enormously. Farmers waiting 5 seconds for a reply will hang up.

**Why MongoDB and not PostgreSQL?**
Crop data, market prices, and equipment listings have wildly different schemas. MongoDB's flexible documents let us iterate rapidly during a hackathon without migrations.

**Graceful Degradation:**
If MongoDB drops, the backend falls back to hardcoded static JSON — so a farmer in a village with spotty connectivity never sees a crash.

---

## 🌍 Impact & Scale

| Metric | Value |
|--------|-------|
| 🇮🇳 Target users | 100M+ small & marginal farmers |
| 📵 Feature phone compatible | Yes (JioPhone, Nokia, KaiOS) |
| 🗣️ Languages supported | 5 (EN, HI, KN, TE, TA) |
| 📶 Minimum connectivity | 2G / EDGE |
| 💰 Cost to farmer | Free |
| 🌐 Offline capability | Partial (PWA cache) |

---

## 👥 Team BelAI

Built with ❤️ for the farmers of Bharat at **SJCIT Hackathon 2026**.

---

## 📄 License

MIT License © 2026 BelAI Team — Free to use, fork, and build upon.

---

<div align="center">

**If BelAI can help even one farmer save their harvest, it's worth it.**

⭐ Star this repo if you believe in AI for social good ⭐

</div>

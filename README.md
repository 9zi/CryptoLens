# CryptoLens

**An accessible, AI-powered cryptocurrency price tracker** — built as a university project.
Author: **Nathan Etwi-Yeboah**

## Features

| Feature | Technology |
|---------|-----------|
| Real-time prices | CoinGecko API + WebSocket |
| Trend analysis | RSI + 24h momentum signals |
| Sentiment analysis | TextBlob NLP + crypto lexicon |
| Price prediction | Scikit-learn LinearRegression |
| AI chat assistant | Groq API (Llama 3.3 70B) |
| Accessibility | WCAG 2.1 AA (high contrast, colour blindness modes, keyboard nav) |

## Project Structure

```
MainProject/
├── backend/
│   ├── main.py              # FastAPI entry point
│   ├── requirements.txt
│   ├── .env.example         # Copy to .env and add your Groq key
│   ├── api/                 # Route handlers
│   │   ├── prices.py
│   │   ├── trends.py
│   │   ├── sentiment.py
│   │   ├── prediction.py
│   │   └── chat.py
│   ├── services/            # Business logic
│   │   ├── coingecko.py
│   │   ├── sentiment.py
│   │   ├── predictor.py
│   │   └── chat_ai.py
│   └── models/
│       └── schemas.py
└── frontend/
    ├── index.html
    ├── css/
    │   ├── main.css
    │   └── accessibility.css
    └── js/
        ├── app.js
        ├── accessibility.js
        ├── charts.js
        └── chat.js
```

## Quick Start

### 1. Set up the backend

```bash
cd backend

# Create a virtual environment
python3 -m venv .venv
source .venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Download TextBlob corpus (one-time)
python -c "import nltk; nltk.download('punkt'); nltk.download('averaged_perceptron_tagger')"

# Add your Groq API key (optional – chat works without it in demo mode)
cp .env.example .env
# Then edit .env and set GROQ_API_KEY
# Get a free key at: https://console.groq.com

# Start the server
uvicorn main:app --reload --port 8000
```

### 2. Open the frontend

Visit **http://localhost:8000** in your browser.

- The backend serves the frontend automatically.
- The interactive API docs are at **http://localhost:8000/docs**

## Set Up On Another Machine

1. Install Python 3.12+.
2. Clone/copy the project folder.
3. From `backend/`, create and activate a virtual environment.
4. Install dependencies and optionally set `GROQ_API_KEY` in `.env`.
5. Run `uvicorn main:app --reload --port 8000`.
6. Open `http://localhost:8000`.

Quick command block:

```bash
git clone <your-repo-url> CryptoLens
cd CryptoLens/backend
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt -r requirements-dev.txt
cp .env.example .env
uvicorn main:app --reload --port 8000
```

## API Endpoints

| Endpoint | Description |
|----------|------------|
| `GET /api/prices` | Current prices for top 10 coins |
| `GET /api/prices/{id}/history?days=7` | Historical price data |
| `GET /api/prices/{id}/detail` | Detailed coin info |
| `GET /api/trends` | CoinGecko trending coins |
| `GET /api/trends/analysis` | RSI + momentum signals |
| `GET /api/sentiment/{id}` | NLP sentiment for a coin |
| `GET /api/predict/{id}` | 24h + 7d price prediction |
| `POST /api/chat` | AI chat assistant |
| `WS /ws/prices` | WebSocket live price feed |

## Accessibility Features

- ♿ **WCAG 2.1 AA** compliant
- 🔊 Screen reader support (ARIA live regions, landmarks, labels)
- ⌨️ Full keyboard navigation with visible focus indicators
- 🌓 High contrast mode
- 🎨 Colour blindness simulation (Protanopia, Deuteranopia, Tritanopia)
- 📖 Dyslexia-friendly font toggle
- ⏸ Reduced motion toggle (also respects system preference)
- 📋 Accessible data tables as alternative to charts

## Report Topics

This project covers:
1. **RESTful API design** with FastAPI
2. **Real-time systems** with WebSockets
3. **Machine learning** (LinearRegression for time series)
4. **NLP / Sentiment analysis** (TextBlob + custom lexicon)
5. **AI integration** (Groq API, prompt hardening)
6. **Web accessibility** (WCAG standards)
7. **API integration** with caching and rate limiting
8. **Inclusive design** principles

---

*Data from [CoinGecko](https://coingecko.com). Not financial advice.*

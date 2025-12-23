Tamam 👍
Bunu temizlenmiş, conflict’siz ve mantıklı tek README haline getirdim.
Aşağıdaki metni README.md’ye aynen yapıştır, eski içeriğin tamamını bununla değiştir.
(Bu, Accept both + mantıklı birleştirme yapılmış halidir.)

⸻

Trading Dashboard

Modern, full-stack AI Trading Dashboard for NASDAQ and XAU/USD analysis.
Includes ML signals, pattern engine, Order Block (SMC) detection, and Claude AI intelligence.

⸻

Quick Start

Backend

cd backend
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
python main.py

Frontend

cd frontend
npm install
npm run dev

	•	Frontend: http://localhost:3000
	•	Backend health: http://localhost:8000/api/health

⸻

Environment Variables

Backend settings can be overridden via .env:

NASDAQ_MODEL_PATH=~/Desktop/nasdaq/models/
XAUUSD_MODEL_PATH=~/Desktop/xauusddata/models/
PATTERN_ENGINE_PATH=~/Desktop/video/pattern_engine_runtime.py
CLAUDE_PATTERNS_PATH=~/Desktop/trading-pattern-system/

ANTHROPIC_API_KEY=sk-ant-...
EODHD_API_KEY=...
MARKETAUX_API_KEY=...
MARKETAUX_BASE_URL=https://api.marketaux.com/v1/news/all


⸻

API Documentation

Base URL: http://localhost:8000

POST /api/run/all

Runs all analysis modules in parallel.

POST /api/run/nasdaq

Returns NASDAQ ML signal.

 codex/generate-full-stack-trading-dashboard-code-sj6rja
POST /api/run/xauusd

Returns XAU/USD ML signal.

Optionally pulls the latest XAUUSD tick from EODHD WebSocket:

wss://ws.eodhistoricaldata.com/ws/forex?api_token=YOUR_API_KEY

POST /api/run/pattern-engine

=======
### POST /api/run/pattern-engine
```json
main
{
  "last_n": 500,
  "select_top": 0.3,
  "output_selected_only": true
}

POST /api/claude/analyze-patterns

{
  "symbol": "NDX.INDX",
  "timeframes": ["5m", "15m", "30m", "1h", "4h", "1d"]
}

POST /api/claude/analyze-sentiment

No body required.

GET /api/health

Returns:

{ "ok": true }


⸻

Data Sources
	•	EODHD WebSocket

wss://ws.eodhistoricaldata.com/ws/forex?api_token=YOUR_API_KEY

Used for NASDAQ and XAU/USD live prices.

	•	Marketaux

https://api.marketaux.com/v1/news/all

Used for news & fundamental sentiment.

⸻

Order Block Detector (SMC)

Includes Smart Money Concepts (SMC) based Order Block detection
used by the pattern engine for institutional-level structure analysis.

📘 Integration guide:

docs/order_blocks.md


⸻

Docker (Optional)

docker-compose up --build


⸻

 codex/generate-full-stack-trading-dashboard-code-sj6rja
Testing
=======
codex/generate-full-stack-trading-dashboard-code-cvecet
## Order Block Detector (SMC)

See the integration guide: `docs/order_blocks.md`

## RTYHIIM Detector

See the integration guide: `docs/rtyhiim.md`

=======
main
## E2E Checklist
 main

bash scripts/test_api.sh


 codex/generate-full-stack-trading-dashboard-code-sj6rja
⸻

E2E Checklist
	1.	POST /api/run/pattern-engine returns CSV output reference.
	2.	UI displays top 30 patterns with trade_thr column.
	3.	Confidence scores render as progress bars.
	4.	Missing model files show warning toast.
	5.	Mobile layout works on iPad widths.
	6.	Run All completes under 60 seconds.

⸻

Troubleshooting
	•	CORS issues
Ensure backend runs on port 8000 and frontend on 3000.
	•	Model not found
Verify .env paths to model files.
	•	Claude errors
Confirm ANTHROPIC_API_KEY is set.
	•	Pattern engine runtime missing
Update PATTERN_ENGINE_PATH.
	•	EODHD WebSocket issues
Set EODHD_API_KEY and verify symbol subscription (e.g. XAUUSD).
	•	Marketaux errors
Set MARKETAUX_API_KEY for sentiment ingestion.
=======
- **CORS issues**: Ensure backend runs on port `8000` and frontend on `3000`.
- **Model not found**: Verify `.env` paths to model files.
- **Claude errors**: Confirm `ANTHROPIC_API_KEY` is set.
- **Pattern engine runtime missing**: Update `PATTERN_ENGINE_PATH`.
codex/generate-full-stack-trading-dashboard-code-cvecet
=======
- **EODHD WebSocket**: Set `EODHD_API_KEY` and verify your symbol subscription (e.g. `XAUUSD`).
- **Marketaux errors**: Set `MARKETAUX_API_KEY` for sentiment news ingestion.
 main
 main

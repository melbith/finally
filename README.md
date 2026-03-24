# FinAlly — AI Trading Workstation

AI-powered trading workstation with live market data, simulated portfolio trading, and an LLM chat assistant that analyzes positions and executes trades via natural language. Built entirely by coding agents as a capstone for an agentic AI coding course.

## Status

**In progress.** Market data backend is complete (simulator + real data). Remaining: database, API routes, frontend, AI chat, Docker packaging.

## What's Built

- **Market data subsystem** (`backend/app/market/`) — GBM simulator with correlated sector moves, Massive/Polygon.io REST client, unified interface via strategy pattern, thread-safe price cache, SSE streaming endpoint. 73 tests passing, 84% coverage.

## Planned Features

- Live price streaming with green/red flash animations
- $10k simulated portfolio with market orders
- Portfolio heatmap, P&L chart, positions table
- AI chat assistant that auto-executes trades
- Watchlist management (manual + via AI)
- Bloomberg-inspired dark terminal UI

## Architecture

Single Docker container on port 8000:

- **Frontend**: Next.js (static export), TypeScript, Tailwind CSS
- **Backend**: FastAPI (Python/uv), SSE streaming, SQLite
- **AI**: LiteLLM → OpenRouter (Cerebras inference), structured outputs
- **Market data**: GBM simulator (default) or Massive API (optional)

## Project Structure

```
finally/
├── backend/     # FastAPI uv project (market data complete)
├── planning/    # Project docs and agent contracts
├── frontend/    # Next.js static export (not yet created)
├── test/        # Playwright E2E tests (not yet created)
├── db/          # SQLite volume mount (runtime)
└── scripts/     # Start/stop helpers (not yet created)
```

## Environment Variables

| Variable | Required | Description |
|---|---|---|
| `OPENROUTER_API_KEY` | Yes | OpenRouter API key for AI chat |
| `MASSIVE_API_KEY` | No | Massive (Polygon.io) key for real data; omit for simulator |
| `LLM_MOCK` | No | `true` for deterministic mock LLM responses (testing) |

## License

See [LICENSE](LICENSE).

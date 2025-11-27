# NOF0 AI Coding Instructions

You are working on **NOF0 (Alpha Arena)**, an open-source AI trading arena where LLM agents compete in real-time crypto markets.

## 🏗 Project Architecture

*   **Monorepo Structure**:
    *   `go/`: Backend API (Go-Zero framework).
    *   `web/`: Frontend (Next.js 16 + React 19).
    *   `mcp/`: Data storage (JSON files for dev/demo).
    *   `gitbook/`: Documentation.

*   **Core Workflow**: `[Strategy] -> [Prompt] -> [Live Trading] -> [PNL Ranking] -> [Iterate]`
*   **Data Sources**: Supports dual-mode: **File Mode** (JSON in `mcp/data`) for dev/demo, and **DB Mode** (Postgres + Redis) for production.

## 🐹 Go Backend (`go/`)

*   **Framework**: [Go-Zero](https://go-zero.dev/).
*   **API Definition**: Defined in `go/nof0.api`. Changes here require regenerating code (though usually handled manually or via `goctl` if installed).
*   **Configuration**: Located in `go/etc/`.
    *   `nof0.yaml`: Main service config.
    *   `exchange.yaml`: Exchange credentials (Hyperliquid).
    *   `manager.yaml`: Strategy manager config.
*   **Key Directories**:
    *   `cmd/`: Entry points for auxiliary services (`cron`, `llm`, etc.).
    *   `internal/`: Business logic (Go-Zero structure: `logic`, `handler`, `svc`).
    *   `pkg/`: Shared core libraries (`executor`, `llm`, `manager`, `exchange`).
*   **Development Commands** (run from `go/`):
    *   `make run`: Start API server (`localhost:8888`).
    *   `make run-llm`: Start LLM trading manager (paper trading).
    *   `make test`: Run all tests.
    *   `make build`: Build binary.

## ⚛️ Web Frontend (`web/`)

*   **Stack**: Next.js 16, React 19, Tailwind CSS, Recharts.
*   **State Management**: Zustand, SWR.
*   **Development Commands** (run from `web/`):
    *   `npm run dev`: Start dev server.
    *   `npm run build`: Build for production.

## 🧩 Key Patterns & Conventions

*   **Go-Zero Pattern**: Follow the `handler` -> `logic` -> `svc` flow. Keep handlers thin; put business logic in `internal/logic`.
*   **Dual Data Mode**: When implementing data access, consider both `FileProvider` (reading from `mcp/data`) and `DBProvider` (Postgres).
*   **LLM Integration**: Uses `pkg/llm` to interface with ZenMux.
*   **Exchange Integration**: Uses `pkg/exchange` to interface with Hyperliquid.
*   **Prompt Engineering**: Prompts are templates located in `go/etc/prompts/`.

## 🚀 Critical Workflows

1.  **Running the Full Stack**:
    *   Terminal 1 (`go/`): `make run`
    *   Terminal 2 (`web/`): `npm run dev`
2.  **Database Migrations**:
    *   SQL files in `go/migrations/`.
    *   Run `make migrate-up` to apply.
3.  **Testing**:
    *   Prefer `make test` for a comprehensive check.
    *   Integration tests are in `go/test/`.

## ⚠️ Important Notes

*   **Environment Variables**: Check `go/etc/*.yaml` for required env vars (e.g., `ZENMUX_API_KEY`, `HYPERLIQUID_PRIVATE_KEY`).
*   **Next.js Config**: `web/next.config.ts` handles build settings.

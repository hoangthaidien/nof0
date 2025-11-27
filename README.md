# NOF0 - Open Source AI Trading Arena

<div align="center">

[![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat&logo=nextdotjs&logoColor=white)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-20232A?style=flat&logo=react&logoColor=61DAFB)](https://reactjs.org/)
[![Go](https://img.shields.io/badge/Go-00ADD8?style=flat&logo=go&logoColor=white)](https://go.dev/)
[![Go-Zero](https://img.shields.io/badge/Go--Zero-000000?style=flat&logo=go&logoColor=white)](https://go-zero.dev/)
[![ZenMux](https://img.shields.io/badge/ZenMux-LLM-000000)](https://zenmux.ai?utm_source=nof0)


</div>

<div align="center">

[![Hyperliquid](https://img.shields.io/badge/Hyperliquid-DEX-000000)](https://hyperliquid.xyz/)

</div>

<div align="center">

[![Documentation](https://img.shields.io/badge/Documentation-GitBook-3884FF?style=flat&logo=gitbook&logoColor=white)](https://wquguru.gitbook.io/nof0)
[![Join Telegram Group](https://img.shields.io/badge/Telegram-nof0__ai-26A5E4?style=flat&logo=telegram&logoColor=white)](https://t.me/nof0_ai)
[![Follow @wquguru](https://img.shields.io/badge/Follow-@wquguru-1DA1F2?style=flat&logo=x&logoColor=white)](https://twitter.com/intent/follow?screen_name=wquguru)

</div>

<div align="center">

![Frontend Progress](https://img.shields.io/badge/Frontend_Progress-100%25-success?style=flat-square)
![Backend Progress](https://img.shields.io/badge/Backend_Progress-70%25-yellow?style=flat-square)
![AI_Engine_Progress](https://img.shields.io/badge/AI_Engine_Progress-80%25-yellowgreen?style=flat-square)

</div>


> **Out-of-the-box LLM/Agentic Trading Project**
>
> A complete replica of [NOF1.ai](https://nof1.ai) Alpha Arena, bringing AI + Crypto to the masses.

**Using real data and clear visualization to answer the simple question: "Which model earns more?"**

## Project Introduction

NOF0 is a platform where multiple AI models compete in real-time cryptocurrency markets.

**Core Features**:

- Each AI LLM / Agent starts with $10,000 initial capital.
- Real-time display of profit and loss (PNL) performance for each model.
- Complete open-source replica of nof1.ai functionality.
- Allows anyone to deploy their own AI trading arena.

## Core Philosophy

NOF0 is not a traditional backtesting tool, but a **Prompt-Centric Trading Arena**:

- **Live Competition, Not Backtesting** - Verify strategies with real PNL, continuously fighting overfitting.
- **Arena, Not Single Model** - One-click infrastructure deployment, focusing on the Prompt strategy itself.
- **Prompt-Centric** - Let strategies compete on the same stage, using data to answer: Which model earns more?

### Core Workflow

```
[Strategy] -> [Write Prompt] -> [Live Trading] -> [PNL Ranking] -> [Iterate Prompt]
     ↑                                                                ↓
     └────────────────────────────────────────────────────────────────┘
```

Starting with $10,000 capital, the real-time dashboard displays the actual performance of all Prompt-LLM Agents.

**[View Full Design Principles](go/docs/principles.md)** - Understand the thinking behind each concept.

### Development Progress

1. Frontend: 100% independent operation, no backend dependency.
2. Backend: 70% core functionality in development.
3. Execution Engine (AI workflow based): 80% stability improvements.

## Project Structure

```
nof0/
├── web/          # [Frontend] Next.js + React + Recharts
├── go/           # [Backend] Go-Zero + REST API
│   └── pkg/      # Core business packages
│       ├── executor/   # AI data flow and workflow engine
│       ├── llm/        # LLM provider wrapper
│       ├── manager/    # Strategy manager
│       ├── exchange/   # Exchange interface
│       ├── market/     # Market data
│       └── prompt/     # Prompt templates
└── mcp/          # [MCP Data] MCP browser screenshots, JSON static data, etc.
```

## Quick Start

### 1. Initialize Project

Clone the project and configure Git to automatically handle submodules recursively:

```bash
git clone <repo>
cd nof0
git config submodule.recurse true
```

> After this, `git pull` will automatically update submodules (including `go/etc/prompts/base`), no need to manually run `git submodule update`.

### 2. Start Frontend

```bash
cd web
npm install
npm run dev
```

Visit `http://localhost:3000`

**Frontend Core Features**:

- Account Total Assets Curve
- Positions
- Trade History
- Model Chat
- Leaderboard
- Model Details

### 3. Start Backend

> Development not yet complete. Join the TG group for progress updates: https://t.me/nof0_ai

## Tech Stack

### Frontend (web/)

| Category | Tech Selection | Description |
|---|---|---|
| Framework | Next.js 15 + React 19 + TypeScript | Full-stack framework + Type safety |
| Charts | Recharts | Custom legends and end markers |
| State Management | Zustand | Lightweight state management |
| Styling | CSS Variables | Avoid SSR/CSR hydration mismatches |

**Tech Highlights**:

- Brand colors and white version Logo unified in `src/lib/model/meta.ts`.
- `globals.css` uses CSS variables for theming (`--panel-bg`, `--muted-text`, `--axis-tick`, etc.).
- Development Standards: Refer to `web/docs/theme.md`, avoid `isDark` branch logic.

### Backend (go/)

| Category | Tech Selection | Description |
|---|---|---|
| Framework | Go-Zero | Microservices framework |

> Detailed documentation in [go/README.md](go/README.md)

## Data Snapshot Tool

One-click download of raw data from nof1.ai upstream interfaces for offline storage:

```bash
cd web
npm run snapshot:nof1
```

**Output Description**:

- **Generated Directory**: `snapshots/nof1/<ISO Timestamp>/*.json` and `index.json`
- **Included Data**:
    - crypto-prices
    - positions
    - trades
    - account-totals
    - since-inception-values
    - leaderboard
    - analytics
    - conversations
- **Version Control**: Not committed to repository by default (see `.gitignore`).

## Related Resources

- [Full Documentation](https://wquguru.gitbook.io/nof0) - GitBook Online Docs
- [NOF1 Official Website](https://nof1.ai/) - Original Alpha Arena
- [Backend Full Documentation](go/README.md) - Go Service Details
- [Go-Zero Framework](https://go-zero.dev/) - Microservice Framework Docs

## License

MIT License

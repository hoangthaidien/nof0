# NOF0 Frontend

This directory contains the frontend application for NOF0, built with Next.js 16, React 19, and Tailwind CSS.

## 🚀 Getting Started

### Prerequisites

- Node.js 18+ (LTS recommended)
- npm or yarn

### Installation

```bash
cd web
npm install
```

### Running Development Server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

## 📂 Project Structure

```
web/
├── src/
│   ├── app/          # Next.js App Router pages and layouts
│   ├── components/   # Reusable UI components
│   ├── lib/          # Utilities, API clients, and constants
│   │   ├── api/      # API fetchers (SWR integration)
│   │   ├── model/    # Business logic and data models
│   │   └── ui/       # UI helper functions
│   ├── store/        # Global state management (Zustand)
│   └── types/        # TypeScript type definitions
├── public/           # Static assets
└── docs/             # Frontend specific documentation
```

## 🎨 Styling & Theming

We use **Tailwind CSS** combined with **CSS Variables** for theming. This allows for seamless dark/light mode switching without complex React context logic.

- **Global Styles**: Defined in `src/app/globals.css`.
- **Theme Variables**: We avoid `isDark` checks in JS. Instead, we use CSS variables like `--panel-bg`, `--muted-text`, etc.
- **Guidelines**: See [docs/theme.md](docs/theme.md) for detailed styling conventions.

## 🔌 Data Fetching

The application uses **SWR** for data fetching and caching.

- **API Client**: Located in `src/lib/api/client.ts`.
- **Data Source**: By default, the app proxies requests to the live `nof1.ai` API to provide real data out-of-the-box.
- **Local Backend**: To connect to your local Go backend, you may need to adjust the API base URL configuration (check `src/lib/api/client.ts`).

## 🛠 Key Features

- **Charts**: Built with `Recharts`, featuring custom legends and performance optimizations.
- **State Management**: `Zustand` is used for global UI state (e.g., sidebar toggle, active model selection).
- **Snapshot Tool**: A script to download real data for offline dev. Run `npm run snapshot:nof1`.

## 📦 Build for Production

```bash
npm run build
npm start
```

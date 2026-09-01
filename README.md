# Tokenized Stocks

A modern dashboard for exploring and comparing **tokenized equities** using live market data.

Built with **Next.js, TypeScript and Tailwind CSS**, the project focuses on reliable external API integration, normalized financial data and a responsive fintech-oriented user experience.

## Overview

Tokenized Stocks provides a unified interface for monitoring tokenized equities and comparing market data across supported assets.

The application retrieves data from external market-data providers, validates and normalizes the responses, and exposes the information through a responsive dashboard.

The project also explores production-oriented frontend and API engineering patterns such as provider fallback, runtime validation, rate limiting and automated testing.

## Features

- Live tokenized stock market data
- Kraken as the primary market-data provider
- CoinGecko fallback integration
- Search, sorting and pagination
- Token comparison
- Watchlist support
- Portfolio tracking
- Price alerts
- CSV export
- Dark mode
- Responsive interface
- Newsletter integration
- Affiliate-link configuration

## Data Architecture

Market data flows through a normalized API layer before reaching the frontend.

```text
Kraken API
    │
    ├── success ──────────────┐
    │                         │
    └── failure               ▼
          │             Runtime validation
          ▼                   │
    CoinGecko API             ▼
                        Normalization
                              │
                              ▼
                        Next.js API
                              │
                              ▼
                          Dashboard
```

External API responses are validated before being transformed into a common application model.

This allows the frontend to consume a consistent data structure regardless of the upstream provider.

## Reliability

The API layer includes several defensive mechanisms for handling external services:

- Request timeouts
- Retry logic
- Circuit-breaker behavior
- Rate limiting
- Runtime schema validation
- Safe numeric handling
- Provider fallback
- Error-state handling

## Tech Stack

### Frontend

- **Next.js 14**
- **React 18**
- **TypeScript**
- **Tailwind CSS**
- **Radix UI**
- **Framer Motion**
- **Recharts**
- **SWR**

### Data & Validation

- **Kraken API**
- **CoinGecko API**
- **Zod**
- **big.js**

### Testing

- **Vitest**
- **Testing Library**
- **Playwright**

## Project Structure

```text
.
├── app/                    # Next.js pages and API routes
├── components/             # Reusable UI components
├── data/                   # Static application configuration
├── docs/                   # Technical documentation
├── lib/
│   ├── fetchers/           # External API integrations
│   ├── affiliates.ts       # Affiliate configuration
│   ├── normalize.ts        # Data normalization
│   ├── tokens.ts           # Supported token definitions
│   └── types.ts            # Types and runtime schemas
├── public/                 # Static assets
├── tests/                  # Tests
└── package.json
```

## Getting Started

### Requirements

- Node.js 18+
- npm

### Installation

Clone the repository:

```bash
git clone https://github.com/Skydax-IT/tokenized-stocks.git
cd tokenized-stocks
```

Install dependencies:

```bash
npm install
```

Create your local environment file:

```bash
cp .env.example .env.local
```

Start the development server:

```bash
npm run dev
```

Then open:

```text
http://localhost:3000
```

## Environment Variables

Example configuration:

```env
BEEHIIV_API_KEY=
BEEHIIV_PUBLICATION_ID=

KRAKEN_API_URL=https://api.kraken.com
COINGECKO_API_URL=https://api.coingecko.com

NEXT_PUBLIC_SITE_URL=http://localhost:3000
```

Do not commit production credentials to the repository.

## Available Commands

```bash
npm run dev
npm run build
npm run start
npm run lint
npm run test
npm run test:coverage
npm run test:e2e
```

## Testing

Run unit tests:

```bash
npm run test
```

Run test coverage:

```bash
npm run test:coverage
```

Run end-to-end tests:

```bash
npm run test:e2e
```

## Security

The application includes several application-level safeguards:

- Input and response validation
- Rate limiting
- Security headers
- Server-side environment variables
- Anti-spam controls for newsletter submissions
- Controlled handling of upstream API failures

Additional technical details are available in the `docs/` directory.

## Design System

The interface uses a custom fintech-oriented design system built on top of Tailwind CSS and Radix UI primitives.

Additional design documentation is available in:

```text
DESIGN_SYSTEM.md
```

## Project Status

This repository is an experimental fintech application and technical portfolio project.

It demonstrates a modern Next.js architecture, external API integration, runtime validation, automated testing and resilience patterns.

It is not intended to execute trades or provide investment recommendations.

## Disclaimer

The information displayed by this application is provided for educational and informational purposes only.

Nothing in this repository constitutes financial or investment advice.

## Author

**Skydax-IT**

## License

MIT
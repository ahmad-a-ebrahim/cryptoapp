# Cryptoverse (cryptoapp)

A React single-page app for browsing live cryptocurrency stats, coin details with price history charts, and the latest crypto news.

**Live demo:** https://ahmad-ebrahim-1.github.io/cryptoapp

## Project Status

| Area | Status |
| --- | --- |
| Homepage (global stats + top coins + news preview) | Implemented |
| Cryptocurrencies list (search) | Implemented |
| Coin details (stats, line chart, time period selector) | Implemented |
| News feed | Implemented |
| Navigation / routing | Implemented, recently fixed |
| Automated tests | Not written yet |
| Secrets management | Needs work (see Known Issues) |

_Last updated: 2026-11-06_

## Tech Stack

- **React 18** (Create React App / `react-scripts` 5)
- **Redux Toolkit + RTK Query** for state and API data fetching
- **React Router v6** for routing
- **Ant Design 5** and `@ant-design/icons` for UI
- **Chart.js 4** with `react-chartjs-2` for price charts
- `millify` and `moment` for number and date formatting
- `gh-pages` for deployment to GitHub Pages

## Routes

| Path | Component | Description |
| --- | --- | --- |
| `/cryptoapp` | `Homepage` | Global stats and top coins |
| `/cryptocurrencies` | `Cryptocurrencies` | Full coin list |
| `/crypto/:coinId` | `CryptoDetails` | Coin stats and history chart |
| `/news` | `News` | Crypto news articles |

## Project Structure

```
src/
├── App.js                  # Layout and routes
├── index.js                # Entry point
├── app/store.js            # Redux store
├── components/             # Navbar, Homepage, Cryptocurrencies,
│                           # CryptoDetails, LineChart, News, Loader
├── services/
│   ├── cryptoApi.js        # Coinranking (RapidAPI) endpoints
│   └── cryptoNewsApi.js    # Bing News Search (RapidAPI) endpoints
└── images/
```

## Getting Started

Prerequisites: Node.js and npm.

```bash
npm install
npm start        # dev server at http://localhost:3000
```

### Scripts

| Command | Description |
| --- | --- |
| `npm start` | Run the app in development mode |
| `npm run build` | Create a production build in `build/` |
| `npm test` | Run tests in watch mode |
| `npm run deploy` | Build and publish to GitHub Pages |

## Data Sources

Both APIs are accessed through [RapidAPI](https://rapidapi.com):

- Coinranking: coins, coin details, coin price history
- Bing News Search: crypto news

## Known Issues / TODO

- The RapidAPI key is hardcoded in `src/services/cryptoApi.js` and `src/services/cryptoNewsApi.js`. Move it to an environment variable (e.g. `REACT_APP_RAPID_API_KEY`) and rotate the exposed key. Note that any key shipped in a client-side bundle is still visible to users.
- No automated tests yet.
- The homepage route is `/cryptoapp` (matching the GitHub Pages path), so the app has no `/` route.

## Maintaining this README

Update the status table, routes and TODO list whenever a commit changes features, routes, dependencies or setup steps.

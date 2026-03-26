# 🌍 GitGlobe

> An interactive 3D globe that visualizes GitHub activity by country in real time.

![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)

---

## Features

- **Interactive 3D globe** — drag to rotate, scroll to zoom, auto-rotation
- **Animated pulse points** — size and glow intensity scaled by commit volume
- **Hover tooltips** — country-level stats: commits, repos, active devs, top language
- **Live sidebar** — top 10 countries ranked by activity
- **Spatial dark theme** — star field background, atmosphere glow, graticule grid
- **Pluggable data layer** — ready to connect to GitHub Archive or GitHub REST API

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Framework | [Next.js 16](https://nextjs.org/) — App Router, Server Components |
| 3D Rendering | [Three.js](https://threejs.org/) + [@react-three/fiber](https://docs.pmnd.rs/react-three-fiber) |
| 3D Helpers | [@react-three/drei](https://github.com/pmndrs/drei) — OrbitControls, Stars, etc. |
| Language | TypeScript — strict mode |
| Styling | Tailwind CSS |

---

## Getting Started

### Prerequisites

- Node.js 18+
- npm or yarn

### Installation

```bash
# Clone the repository
git clone https://github.com/ANDRIANALISOA-sylvere/GitGlobe.git
cd GitGlobe

# Install dependencies
npm install

# Start the development server
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) to see the globe.

---

## Project Structure

```
gitglobe/
├── app/
│   ├── page.tsx              # Main page
│   └── api/
│       └── stats/
│           └── route.ts      # GitHub data endpoint (Node.js)
├── components/
│   ├── Globe.tsx             # Main Three.js globe component
│   ├── CountryPoint.tsx      # Animated green dots
│   └── Tooltip.tsx           # Hover tooltip
├── lib/
│   ├── geoUtils.ts           # lat/lng → 3D coordinates
│   └── githubData.ts         # Data fetch & transformation
└── data/
    └── countries.json        # Country coordinates + mock data
```

---

## Data Sources

By default, GitGlobe uses **mocked static data** to get started quickly.

To plug in real data, update `lib/githubData.ts` with one of:

- **[GitHub Archive](https://www.gharchive.org/)** — public event data, updated hourly
- **[GitHub REST API](https://docs.github.com/en/rest)** — live data (rate limited)
- **Custom JSON/CSV** — your own dataset

---

## Roadmap

- [x] Interactive 3D globe with rotation & zoom
- [x] Animated pulse points per country
- [x] Hover tooltips with country stats
- [x] Top countries sidebar
- [ ] Connect to GitHub Archive (real data)
- [ ] Filter by programming language
- [ ] Filter by time period
- [ ] Click on country for detailed panel
- [ ] Animated arcs between collaborating countries
- [ ] Dark / light theme toggle

---

## Architecture

GitGlobe follows a clear separation between backend and frontend:

```
Next.js API Route (Node.js)
    └── Fetches & transforms GitHub data
    └── Exposes clean JSON: { country, commits, repos, devs, lang }

Three.js (React frontend)
    └── Reads JSON
    └── Converts lat/lng to 3D sphere coordinates
    └── Renders animated points on the globe
```

---

## License

MIT © [ANDRIANALISOA-sylvere](https://github.com/ANDRIANALISOA-sylvere)

---

Built with ❤️ by [ANDRIANALISOA-sylvere](https://github.com/ANDRIANALISOA-sylvere)
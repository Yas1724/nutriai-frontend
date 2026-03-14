# NutriAi Frontend

> AI-powered nutrition tracker — React + Vite, deployed on Vercel.

---

## What is NutriAi?

NutriAi is a full-stack nutrition tracking web app that lets users log meals, track daily macros, and classify food using AI image recognition. This repository contains the frontend only.

---

## Features

- 🔐 **Auth** — Signup, login, email verification, forgot/reset password
- 🧭 **Onboarding** — 7-step personalized setup (goal, body stats, activity level, target weight, timeline with realistic goal validation)
- 📊 **Dashboard** — Daily calorie ring, macro bars, week strip date picker, meal log by slot
- 📸 **Camera** — Snap a meal photo → AI identifies the food → logs macros instantly
- 📈 **Progress** — Daily / weekly / monthly nutrition analytics with shareable public links
- 👤 **Profile** — BMI card, daily targets, body stats, dark/light theme toggle
- 🌗 **Themes** — Pure black & white dark and light mode

---

## Tech Stack

| Layer | Tech |
|---|---|
| Framework | React 18 + Vite |
| Routing | React Router v6 |
| Styling | Inline styles + CSS variables (no external UI lib) |
| Font | DM Sans + Inter (Google Fonts) |
| Auth | JWT via httpOnly cookies |
| API | REST — Node.js + Express backend |
| ML | FastAPI (Python) — ConvNeXt Tiny food classifier |

---

## Project Structure

```
frontend/
├── public/
│   └── nutriai-icon.svg
├── src/
│   └── App.jsx          ← entire app in one file
├── index.html
├── vite.config.js
├── vercel.json          ← SPA routing config
└── package.json
```

---

## Getting Started

### Prerequisites
- Node.js 18+
- Backend running on port 3000
- ML service running on port 8000 (optional)

### Install
```bash
npm install
```

### Environment Variables
Create a `.env` file in the `frontend/` root:
```
VITE_API_URL=http://localhost:3000
VITE_ML_URL=http://localhost:8000
```

### Run locally
```bash
npm run dev
```

### Build for production
```bash
npm run build
```

---

## Deployment (Vercel)

1. Push this repo to GitHub
2. Import on [vercel.com](https://vercel.com)
3. Set **Root Directory** → `frontend/`
4. Add environment variables in Vercel dashboard:
   - `VITE_API_URL` → your backend URL
   - `VITE_ML_URL` → your ML service URL
5. Deploy

The `vercel.json` handles SPA routing so direct URL access (e.g. `/dashboard`) doesn't 404.

---

## Backend

The backend (Node.js + Express + PostgreSQL) is in a separate repository. It handles auth (JWT, bcrypt, email verification via Resend), food log CRUD, nutrition lookup, and share link generation.

---

## Security

- JWT stored in `httpOnly` cookies (not localStorage)
- `helmet` for HTTP security headers
- Rate limiting on auth endpoints (production only)
- Input validation on both client and server
- Share links expire after 7 days
- File upload limited to images under 10MB

---

## License

MIT

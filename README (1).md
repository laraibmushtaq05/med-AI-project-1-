# GlucoGuide

A personal diabetes self-management app that helps people track blood glucose, meals, and medications in one place — and get plain-language insights into their own patterns.

**Live Demo:** [https://bolt.new/p/69329453](https://bolt.new/p/69329453)

---

## Problem

Managing diabetes day-to-day means juggling glucose readings, meal timing, and medication schedules across notebooks, spreadsheets, or disconnected apps. GlucoGuide brings this into a single, private, easy-to-use tool so people can see their trends clearly and understand what their numbers actually mean — without needing to be a data analyst.

---

## Features

- **Secure accounts** — sign up / sign in / sign out, with each user's data kept private via row-level security (RLS) enforced at the database level
- **Glucose logging** — record readings with value, context (e.g. fasting, after-meal), timestamp, and notes
- **Meal logging** — track meal name, type, carbs, and calories
- **Medication logging** — record medication name, dose, and time
- **Dashboard** — 30-day average glucose, percentage of readings in target range, and an interactive glucose trend chart with personalized target lines
- **AI Insights** — generates a short, friendly summary of recent patterns plus one practical, non-medical lifestyle suggestion
- **Custom settings** — set diabetes type and personal glucose targets, which flow through to the dashboard and chart

---

## AI Insights — System Prompt

The AI Insights feature is powered by a server-side edge function using a system prompt designed to keep responses supportive and safe:

> Be friendly and encouraging. Summarize the user's glucose averages and patterns in plain language. Suggest one small, practical lifestyle change. Never recommend medication changes or give specific medical advice — always encourage the user to consult their healthcare provider for medical decisions.

The AI model is served through **Pollinations AI**, a keyless provider — so the app works out of the box with no API key setup required.

---

## Tech Stack

- **Frontend:** React + TypeScript + Vite
- **Styling:** Tailwind CSS
- **Database & Auth:** Supabase (Postgres, Row-Level Security)
- **Serverless:** Supabase Edge Functions
- **AI Provider:** Pollinations AI (keyless text API)

---

## Screenshots

| Dashboard | Dashboard (AI Insights + logs) | Settings |
|---|---|---|
| ![Dashboard](screenshots/dashboard.jpg) | ![Dashboard AI Insights](screenshots/dashboard-insights.jpg) | ![Settings](screenshots/settings.jpg) |

---

## Getting Started

### Prerequisites
- Node.js (v18+)
- A Supabase project (free tier is fine)

### Setup

```bash
# Clone the repo
git clone <your-repo-url>
cd glucoguide

# Install dependencies
npm install

# Configure environment variables
cp .env.example .env
# Fill in your Supabase URL and anon key in .env
```

### Environment Variables

```
VITE_SUPABASE_URL=your_supabase_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
```

> `.env` is gitignored. Only `.env.example` with placeholder values is committed.

### Run locally

```bash
npm run dev
```

### Build for production

```bash
npm run build
```

---

## Database Schema

| Table | Purpose |
|---|---|
| `profiles` | User profile, diabetes type, glucose targets |
| `glucose` | Blood glucose readings (value, context, timestamp, notes) |
| `meals` | Logged meals (name, type, carbs, calories) |
| `meds` | Logged medications (name, dose, time) |

All tables are protected with Row-Level Security so users can only read and write their own data.

---

## Disclaimer

GlucoGuide is a self-management and tracking tool, not a medical device. It does not diagnose conditions or provide medical advice. Always consult a qualified healthcare provider for medical decisions.

---

## License

[MIT](LICENSE) — or replace with your preferred license.

# Adaptive Learning: Netlify frontend + Render API

## 1. Push to GitHub
Keep this layout (`backend/`, `frontend/`, `netlify.toml`) in one repo.

## 2. Render (backend)
1. New **PostgreSQL** database. Copy its **Internal Database URL**.
2. New **Web Service** from the repo: Root Directory `backend`, Build `npm install`, Start `npm start`.
3. Environment variables (see `backend/.env.example`): `DATABASE_URL`, `JWT_SECRET` (long random), `ANTHROPIC_API_KEY`, `INVITE_CODE`, `FRONTEND_URL` (set after step 3). Check `/health` works.

## 3. Netlify (frontend)
1. Edit `frontend/config.js` and put your Render service URL in it, then commit.
2. New site from the repo. `netlify.toml` already sets publish dir to `frontend`; no build command needed.
3. Copy the Netlify URL back into Render as `FRONTEND_URL` (no trailing slash) and redeploy the API.

## 4. Use
Open the site, choose **Create account** with your invite code, upload PDFs, set the date and daily minutes.

## Local dev
`cd backend && cp .env.example .env && npm install && npm run dev`
Serve `frontend/` with any static server (e.g. `npx netlify dev` or `npx serve frontend`), point `config.js` at `http://localhost:3000`, and add the frontend origin to `FRONTEND_URL`.
# learningapp

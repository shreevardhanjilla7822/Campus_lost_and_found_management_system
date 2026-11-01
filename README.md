# Campus Lost & Found Management System

A full-stack campus portal for reporting lost and found items, discovering potential matches, and managing item claims with admin verification.

## Features
- Student registration and login
- Lost/found item reports with photos, location, category, and keywords
- Potential lost/found item matching
- Student dashboard, My Matches, and My Claims
- Admin review for items and claims
- MongoDB persistence and JWT-based authentication

## Project layout
- `client/` — React + Vite frontend
- `server/` — Node.js + Express API
- `SETUP_GUIDE_MAC.md` — beginner-friendly local setup instructions
- `README_ORIGINAL.md` — original project documentation

## Quick start
1. Install Node.js/npm and run MongoDB locally.
2. Configure `server/.env.development` and `client/.env`.
3. In one terminal, run `cd server && npm install && npm run dev`.
4. In another terminal, run `cd client && npm install && npm run dev`.
5. Open `http://localhost:5173`.

For exact commands, MongoDB setup, and troubleshooting, read **SETUP_GUIDE_MAC.md**.

## Claim workflow
Approved found-item details include **View Matches to Claim**, which opens **My Matches**. A student can submit a claim only through the existing match/claim flow.

## Security note
Environment files in this package are for local development only. Change the sample JWT secret and admin password before use, and never commit credentials or real user data.

# Campus Lost & Found — Clean Setup Guide (macOS)

This folder contains the React/Vite frontend and Express/MongoDB backend.

## 1. Requirements
- Node.js and npm
- MongoDB server installed and available locally
- VS Code

## 2. Configure environment files
The ZIP includes development environment files for local testing. Before using it beyond a local demo, change the JWT secret and admin password in `server/.env.development`.

Frontend API URL: `client/.env` → `VITE_API_URL=http://localhost:3001/`
Backend configuration: `server/.env.development` → `DATABASE_URL`, `DATABASE_NAME`, `PORT`, and JWT settings.

## 3. Start MongoDB
Keep this terminal window open. If MongoDB is installed at the path used on this Mac, run:

```bash
mkdir -p "/Users/$(whoami)/Desktop/Campus lost and found/CampusLostFound-main/mongodb-data"
```

Use your own extracted project path in the `--dbpath` argument. For example, if MongoDB is installed in `~/mongodb-macos-aarch64--9.0.4/bin/mongod`:

```bash
"$HOME/mongodb-macos-aarch64--9.0.4/bin/mongod" --dbpath "$HOME/Desktop/Campus lost and found/CampusLostFound-main/mongodb-data" --bind_ip 127.0.0.1 --port 27017
```

If your MongoDB binary or extracted folder is in a different location, update the paths. Do not close the MongoDB terminal while using the app.

## 4. Start the backend
Open a second Terminal window:

```bash
cd "/path/to/CampusLostFound-main/server"
npm install
npm run dev
```

Replace `/path/to/CampusLostFound-main` with the actual folder path. Backend should listen on `http://localhost:3001`.

## 5. Start the frontend
Open a third Terminal window:

```bash
cd "/path/to/CampusLostFound-main/client"
npm install
npm run dev
```

Open the Vite URL shown in the terminal, normally `http://localhost:5173`.

## 6. Claim button behavior
The item details page now shows **View Matches to Claim** for approved found items. Clicking it opens the existing **My Matches** page. A claim still requires an actual match and the existing claim workflow; the button does not automatically submit a claim.

## Troubleshooting
- `ECONNREFUSED 127.0.0.1:27017`: MongoDB is not running or is listening on a different port.
- Frontend cannot reach backend: confirm `server/.env.development` is loaded and `client/.env` points to `http://localhost:3001/`.
- Login/admin issue: admin seeding runs when the backend connects. If an admin account already exists, changing environment credentials will not change that existing account's password.
- If dependencies fail to install, copy the full error from Terminal before changing package versions.

## Important
This is a development project, not a production deployment. Do not publish `.env` files, credentials, uploaded private images, or database contents.

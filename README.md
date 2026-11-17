# Gulliver vs Bolles Scouting Board

The coaches' scouting site: score simulator, season charts, the four battles, rosters, and a PDF download.
It's one static page served by a tiny Node server with no dependencies, so there's nothing to install.

## Deploy on Railway

**Option A: GitHub (easiest to update later)**
1. Put this folder in a new GitHub repo (upload the files, or `git init`, commit, push).
2. In Railway: **New Project → Deploy from GitHub repo** and pick the repo.
3. Railway detects Node and runs `npm start` automatically.
4. Open the service → **Settings → Networking → Generate Domain** to get a public URL.

**Option B: Railway CLI (no GitHub)**
```bash
npm i -g @railway/cli
railway login
railway init        # inside this folder
railway up
railway domain      # creates the public URL
```

## Password-protect it (recommended)

The page has athletes' names and times. To lock it, add these in Railway under **Variables**:

| Variable | Value |
|---|---|
| `SITE_PASSWORD` | any password you choose |
| `SITE_USER` | optional, defaults to `coach` |

Railway redeploys automatically. Visitors then get a browser login box. Leave `SITE_PASSWORD` unset for an open site.
The site also tells search engines not to index it.

## Run locally
```bash
npm start
# open http://localhost:3000
```

## Files
- `public/index.html`: the scouting board
- `public/Gulliver_vs_Bolles_Scouting_Board.pdf`: printable version, linked from the page
- `server.js`: static server (uses Railway's `PORT`; health check at `/healthz`)

To update the board, replace `public/index.html` and redeploy.

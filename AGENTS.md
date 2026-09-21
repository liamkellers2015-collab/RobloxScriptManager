# AGENTS.md

## Project Overview
Static HTML project ("RobloxScriptManager") with two standalone HTML pages:
- `index.html` — Roblox Script Injector UI (RTL, Hebrew)
- `WorldClock.html` — World Clock UI (RTL, Hebrew)

No build step, no backend, no dependencies. Pure static HTML/CSS/JS.

## Running in Base44
Served via `docker compose -f docker-compose.base44.yml up -d` using `nginx:alpine` on host port 3000.

## Key Quirk
The repo root directory has `drwx------` (700) permissions by default, which blocks nginx's non-root worker from traversing the bind mount. Run `chmod 755 .` if you get a 403 Forbidden.

## Verification
- `curl -s -o /dev/null -w "%{http_code}" http://localhost:3000/` → 200
- `curl -s http://localhost:3000/WorldClock.html` → serves the world clock page

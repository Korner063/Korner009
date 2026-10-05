# Korner009 — แอดเทนแดนซ์ (Employee Attendance Admin)

## What this app is
A single-file, fully client-side app: everything lives in `index.html` (~2,250 lines).
Thai-language employee attendance/attendance-check admin dashboard.

- No backend, no build step, no package.json, no framework. Vanilla JS + Tailwind (CDN).
- All dependencies load from CDNs (Tailwind, Google Fonts, Font Awesome, SheetJS for Excel export).
- All data persists in `localStorage` only — no external services, no credentials required.
- `logo-dashboard.png` is referenced by `index.html` and must be served alongside it.

## Running in Base44
`docker compose -f docker-compose.base44.yml up -d` — nginx:1.27-alpine bind-mounts
`index.html` and `logo-dashboard.png` into the docroot and serves them on host port 3000.
No live-reload dev server exists (static file); after editing `index.html`, call
`reload_preview` so the user's preview refreshes.

## Verifying
`curl -s http://localhost:3000/` should return the HTML starting with
`<!DOCTYPE html>` and title `แอดเทนแดนซ์ - ระบบเช็คชื่อพนักงาน`.
Container healthcheck: `wget -q --spider http://localhost:80/index.html`.

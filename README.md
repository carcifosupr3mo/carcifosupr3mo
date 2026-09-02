<h1 align="left">Nathan Pollini</h1>

<p align="left">
  IT infrastructure &amp; systems — apprentice / student, Ticino (Switzerland)<br>
  I build and run my own self-hosted services on a Proxmox homelab, and I write the tooling around them.
</p>

<p align="left">
  <a href="https://photocarcifo.ch"><img alt="Website" src="https://img.shields.io/badge/photocarcifo.ch-live-2f81f7?style=flat-square&logo=googlechrome&logoColor=white"></a>
  <img alt="Location" src="https://img.shields.io/badge/Ticino-Switzerland-6e7681?style=flat-square&logo=googlemaps&logoColor=white">
  <img alt="Focus" src="https://img.shields.io/badge/focus-infrastructure%20%26%20networking-6e7681?style=flat-square">
</p>

---

## About

- Training as an IT specialist at CPT Locarno, focused on infrastructure and systems.
- Most of what I know comes from running things end to end: provisioning containers, reverse proxying, TLS, databases, backups, cron, monitoring — and fixing them when they break.
- Two of my services run in production with real users, which is a very effective teacher about backups.

## Tech

`Python` · `Bash` · `SQL` · `JavaScript`

`FastAPI` · `SQLAlchemy` · `PostgreSQL` · `SQLite` · `MQTT`

`Proxmox` · `Docker` · `LXC` · `Nginx` · `Caddy`

**Currently learning:** CCNA 1–3 (routing, switching, subnetting) · Docker Compose in production · CI/CD with GitHub Actions · PostgreSQL tuning & backup strategy

## Selected projects

### Photocarcifo — [photocarcifo.ch](https://photocarcifo.ch)

Self-hosted photography portfolio and client gallery, in production with real clients.

- FastAPI + SQLite, photos served from a NAS over NFS, Nginx with Let's Encrypt
- **Per-client album isolation**: a signed cookie grants access to one album and its subtree only, never accumulating across albums, with user-selectable link expiry
- Client favourites workflow with per-person download and an admin view
- Two gallery view modes, EXIF rotation correction applied across tens of thousands of mis-recorded vertical photos
- Nightly thumbnail pregeneration across three sizes, rotating backups with automatic restore on failure and free-space checks
- Weekly PDF report by email, auto-generated site map
- **PageSpeed 100** — inlined critical CSS, `fetchpriority` on the LCP image, corrected heading hierarchy
- CSP-compliant: no inline JavaScript anywhere

`FastAPI` · `SQLite` · `Nginx` · `NFS` · `Proxmox LXC`

### Filament Inventory — 3D printing stock & job tracking

Inventory and print-history system for a Bambu Lab P1S with AMS, built to replace manual logging.

- Three-container stack on a Proxmox LXC: PostgreSQL 16, FastAPI/uvicorn, Caddy
- SQLAlchemy 2.0 async models, ~46 endpoints, print job state machine (`IDLE → PREPARE → RUNNING → FINISH/FAILED`)
- Persistent **MQTT supervisor** with delta merging against the live printer, plus an FTPS client with multi-path 3MF resolution
- **Four-tier consumption cascade**: exact grams parsed from the 3MF → proportional estimation → manual upload fallback
- Spools are matched by **material type and colour, not by AMS slot index** — the slot index in the 3MF does not correspond to the physical slot, which took a diagnostic probe against the live printer to establish
- Tabulator.js inventory table on a dark palette where colour is reserved exclusively for filament data; every KPI card and chart segment links through to its filtered view
- CSV import/export, backup rotation, Telegram notifications
- 6 test suites, 178 assertions

`FastAPI` · `PostgreSQL` · `Docker` · `MQTT` · `FTPS` · `Tabulator.js`

### Meteo Arbedo-Castione — [meteo.photocarcifo.ch](https://meteo.photocarcifo.ch)

Self-hosted weather dashboard: MeteoSwiss/Open-Meteo ingestion, automatic storm detection, historical archive with JWT-protected API, webcam timeline, web push and Telegram notifications, PWA build.

`FastAPI` · `PostgreSQL` · `Apache` · `Proxmox LXC`

### Homelab & automation

Proxmox host running the containers above, plus a Piwigo gallery. Scheduled maintenance and update scripts, TLS termination, fail2ban, monitored backups. Alongside it: multithreaded host discovery over a home network in Python (ping with ARP fallback and TTL parsing), and smaller file-management tooling.

`Proxmox` · `Bash` · `cron` · `Python`

> Repositories for these are being published progressively. Infrastructure details, internal addressing and credentials stay private.

## Contribution snake

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/carcifosupr3mo/carcifosupr3mo/output/github-contribution-grid-snake-dark.svg" />
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/carcifosupr3mo/carcifosupr3mo/output/github-contribution-grid-snake.svg" />
  <img alt="contribution snake animation" src="https://raw.githubusercontent.com/carcifosupr3mo/carcifosupr3mo/output/github-contribution-grid-snake.svg" />
</picture>

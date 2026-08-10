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

- Training as an IT specialist (**CPT Locarno**), working on infrastructure and systems.
- Most of what I know comes from running things end to end: provisioning containers, reverse proxying, TLS, databases, backups, cron, monitoring, and fixing them when they break at 23:00.
- Two of my services run in production with real users on them, which is a very effective teacher about backups and about not breaking things at 22:00 on a Friday.
- Currently working through the **Cisco Networking Academy CCNA** track (CCNA 1 → 3).

## Tech

**Languages**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat-square&logo=gnubash&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-336791?style=flat-square&logo=postgresql&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)

**Backend &amp; data**

![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy_2.0_async-D71F00?style=flat-square&logo=sqlalchemy&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL_16-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=flat-square&logo=sqlite&logoColor=white)
![MQTT](https://img.shields.io/badge/MQTT-660066?style=flat-square&logo=mqtt&logoColor=white)

**Systems &amp; virtualization**

![Proxmox](https://img.shields.io/badge/Proxmox_VE-E57000?style=flat-square&logo=proxmox&logoColor=white)
![LXC](https://img.shields.io/badge/LXC-333333?style=flat-square&logo=linuxcontainers&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=flat-square&logo=ubuntu&logoColor=white)
![Synology](https://img.shields.io/badge/Synology_NAS_(NFS)-B5B5B6?style=flat-square&logo=synology&logoColor=black)

**Networking &amp; ops**

![Nginx](https://img.shields.io/badge/Nginx-009639?style=flat-square&logo=nginx&logoColor=white)
![Caddy](https://img.shields.io/badge/Caddy-1F88C0?style=flat-square&logo=caddy&logoColor=white)
![Let's Encrypt](https://img.shields.io/badge/Let's_Encrypt-003A70?style=flat-square&logo=letsencrypt&logoColor=white)
![CSP](https://img.shields.io/badge/CSP_%2F_hardening-1f6feb?style=flat-square)
![Cisco](https://img.shields.io/badge/Cisco_Netacad-1BA0D7?style=flat-square&logo=cisco&logoColor=white)

**Tools**

![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)
![VS Code](https://img.shields.io/badge/VS_Code_(Remote--SSH)-007ACC?style=flat-square&logo=visualstudiocode&logoColor=white)
![Linux CLI](https://img.shields.io/badge/Linux_CLI-FCC624?style=flat-square&logo=linux&logoColor=black)

**Currently learning**

`CCNA 1–3 (routing, switching, subnetting)` · `Docker Compose in production` · `CI/CD with GitHub Actions` · `PostgreSQL tuning & backup strategy`

## Selected projects

### Photocarcifo — [photocarcifo.ch](https://photocarcifo.ch)

Self-hosted photography portfolio and client gallery, in production with real clients.

- FastAPI + SQLite, photos served from a Synology NAS over NFS, Nginx with Let's Encrypt
- **Per-client album isolation**: a signed cookie grants access to one album and its subtree only, never accumulating across albums, with user-selectable link expiry
- Client favourites workflow with per-person download and an admin view
- Two gallery view modes, EXIF rotation correction applied across ~29k mis-recorded vertical photos
- Nightly thumbnail pregeneration across three sizes (~52k files), rotating 3-slot backups with automatic restore on failure and free-space checks
- Weekly PDF report by email, auto-generated site map
- **PageSpeed 100** — inlined critical CSS, `fetchpriority` on the LCP image, corrected heading hierarchy
- CSP-compliant: no inline JavaScript anywhere

`FastAPI` · `SQLite` · `Nginx` · `NFS` · `Proxmox LXC`

### Filament Inventory — 3D printing stock &amp; job tracking

Inventory and print-history system for a Bambu Lab P1S with AMS, built to replace manual logging.

- Three-container stack on a Proxmox LXC: PostgreSQL 16, FastAPI/uvicorn, Caddy
- SQLAlchemy 2.0 async models, ~46 endpoints, print job state machine (`IDLE → PREPARE → RUNNING → FINISH/FAILED`)
- Persistent **MQTT supervisor** with delta merging against the live printer, plus an FTPS client with multi-path 3MF resolution
- **Four-tier consumption cascade**: exact grams parsed from the 3MF → proportional estimation → manual upload fallback
- Spools are matched by **material type + colour, not by AMS slot index** — the slot index in the 3MF does not correspond to the physical slot, which took a diagnostic probe against the live printer to establish
- Tabulator.js inventory table on a dark palette where colour is reserved exclusively for filament data; every KPI card and chart segment links through to its filtered view
- CSV import/export, backup rotation, Telegram notifications
- 6 test suites, 178 assertions

`FastAPI` · `PostgreSQL` · `Docker` · `MQTT` · `FTPS` · `Tabulator.js`

### Meteo Arbedo-Castione — [meteo.photocarcifo.ch](https://meteo.photocarcifo.ch)

Self-hosted weather dashboard: MeteoSwiss/Open-Meteo ingestion, automatic storm detection, historical archive with JWT-protected API, webcam timeline, web push and Telegram notifications, PWA build.

`FastAPI` · `PostgreSQL` · `Apache` · `Proxmox LXC`

### Homelab &amp; automation

Proxmox host running the containers above plus a Piwigo gallery. Scheduled maintenance and update scripts, TLS termination, fail2ban, monitored backups. Alongside it: multithreaded host discovery over a /23 network in Python (ping with ARP fallback and TTL parsing), and smaller file-management tooling.

`Proxmox` · `Bash` · `cron` · `Python`

> Repositories for these are being published progressively. Infrastructure details, internal addressing and credentials stay private.

### 📜 Certificati

* [Visualizza il certificato di Networking Basics](./NetworkingBasicsUpdate20260810-20-d858r1.pdf)

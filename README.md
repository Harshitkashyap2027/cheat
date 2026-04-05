# B25 CHEATS – Free Fire Emote System

> ⚠️ **Disclaimer:** This project is published for **educational and research purposes only.**
> Using third-party tools that interact with Free Fire's game servers violates
> [Garena's Terms of Service](https://ff.garena.com/terms) and may result in a
> permanent account ban or legal consequences. The author does not condone cheating
> in online games. Use this code only to study web technologies and API design.

---

## What Is This?

A single-page web application that demonstrates how a frontend can communicate with
a backend API to send in-game emote actions in Free Fire. It is intended as a
technical reference for understanding:

- How game client actions can be abstracted into REST API calls
- How a paginated emote library can be lazily loaded in the browser
- How region/server selection and multi-UID targeting work in a UI

---

## How It Works

### Architecture

```
Browser (HTML + CSS + JS)
        │
        │  HTTP POST /send_emote
        │  { server, team_code, emote_id, uids[], auto_leave }
        ▼
  Backend API Server  ──►  Free Fire Game Servers
```

### Frontend (`B25 CHEATS - Fast Emote System.html`)

| Feature | Description |
|---|---|
| Emote grid | Displays 344 emotes with lazy loading (50 per page via `/api/load_more_emotes`) |
| Server selector | 16 regional servers (India, Brazil, Europe, etc.) polled via `/api/servers_enabled` |
| UID inputs | Up to 4 Free Fire player IDs can be targeted simultaneously |
| Auto Leave | Instructs the backend to auto-leave the team lobby after sending |
| Lag Mode | Sends a separate request to `/lag` endpoint |
| Theme | Light/dark mode persisted in `localStorage` |

### API Endpoints (Backend – not included in this repo)

| Method | Endpoint | Purpose |
|---|---|---|
| `GET` | `/api/servers_enabled` | Returns which regional servers are active |
| `POST` | `/send_emote` | Sends the selected emote to the given UIDs |
| `POST` | `/lag` | Triggers lag-mode packet |
| `GET` | `/api/load_more_emotes?page=N` | Returns next page of emote objects |
| `GET` | `/api/ads/index` | Loads advertisement data |

### Static Assets

| File | Purpose |
|---|---|
| `all.min.css` | Minified UI stylesheet (flexbox, CSS variables, animations) |
| `stattag.js.download` | Telemetry / analytics script |
| `vignette.min.js.download` | Minified ad/tracking library |
| `*.png` | Emote icon images, named by their in-game emote ID |

---

## Tech Stack

- **Frontend:** Vanilla HTML5, CSS3, JavaScript (no frameworks)
- **API:** RESTful JSON over HTTP
- **Assets:** Static PNG sprites for emote icons

---

## Legal

This project is provided **as-is** for educational purposes. The maintainer is not
responsible for any bans, account suspensions, or legal actions that result from
misuse of this code against live game servers.

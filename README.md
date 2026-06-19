# Stjernekamp ⭐

A Progressive Web App (PWA) reward system for kids. Children earn stars by completing tasks and can spend them on rewards. Parents manage everything through a PIN-protected admin panel.

## Features

- **Three kids** — Trym, Emma and Hermine, each with their own color and star count
- **Tasks** — kids request task completion, parent approves or rejects
- **Rewards** — kids spend earned stars on rewards, parent approves
- **History** — full activity log filterable per kid
- **Admin panel** — PIN-protected, stays unlocked for 30 minutes after login
- **Real-time sync** — powered by Firebase Firestore, all devices update instantly
- **Installable PWA** — works offline shell, add to home screen on iOS/Android

## Tech stack

- Vanilla HTML/CSS/JS — no build step
- [Firebase Firestore](https://firebase.google.com/docs/firestore) for real-time data
- Service worker for PWA shell caching

## Project structure

```
Stjerner/
├── index.html      # Entire app (views, styles, scripts)
├── manifest.json   # PWA manifest
├── sw.js           # Service worker
└── README.md
```

## Firebase setup

1. Create a Firebase project at [console.firebase.google.com](https://console.firebase.google.com)
2. Create a Firestore database (Native mode, `europe-west1`)
3. Copy your project config into `index.html` under `FIREBASE_CONFIG`
4. Set Firestore rules to allow read/write (or lock down as needed)

The app seeds initial data (kids, tasks, rewards, admin PIN) automatically on first load if the database is empty.

## Default admin PIN

`3212` — change it in the admin panel under Settings.

## Firestore collections

| Collection  | Description                              |
|-------------|------------------------------------------|
| `kids`      | Kid profiles (name, color, star count)   |
| `tasks`     | Available tasks (title, emoji, stars, assignedTo) |
| `rewards`   | Available rewards (title, emoji, stars)  |
| `pending`   | Pending approval requests                |
| `history`   | Completed task/reward log                |
| `settings`  | App settings (admin PIN)                 |

## Deployment

The app is a single static HTML file and can be hosted anywhere — GitHub Pages, Netlify, Vercel, or any web server.

# StudyFlow — University Organizer PWA

A Progressive Web App for university students to organize their academic life. Built with vanilla HTML, CSS, and JavaScript, powered by Firebase and AI.

## 🌐 Live App
[studyflow-7su.pages.dev](https://studyflow-7su.pages.dev)

## ✨ Features

- **Dashboard** — Weekly overview, upcoming tasks and exams
- **Schedule** — Visual timetable with real-time current hour indicator
- **Subjects** — Individual pages with 5 tabs: Summary, Tasks, Evaluation, Notes, Calendar
- **Tasks & Exams** — Priority system, filters, due dates, mark as done
- **Evaluation** — Grade calculator with required grade to pass, confetti on approval
- **Notes & Folders** — Google Drive-style with drag & drop, nested folders, breadcrumb
- **Global Calendar** — Click any day to see events, add tasks directly
- **Quick Notes** — Color sticky notes, auto-expire in 7 days
- **Flow AI Assistant** — Full read/write access to your data, powered by Groq
- **Document Upload** — PDF and file storage via Firebase Storage
- **PWA** — Installable on mobile, offline support via Service Worker
- **Real-time Sync** — Data synced across devices via Firestore

## 🤖 Flow — AI Assistant

Flow has full access to your academic data and can:
- Read all subjects, tasks, evaluations, schedule and notes
- Add subjects, tasks and exams to the app
- Register grades in evaluation criteria
- Mark tasks as done
- Always knows today's date and time

Powered by **Groq** (free tier, no credit card required).

## 🛠 Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML + CSS + Vanilla JS (single index.html) |
| Database | Firebase Firestore |
| Auth | Firebase Auth (Google + Email/Password) |
| Storage | Firebase Storage |
| Hosting | Cloudflare Pages |
| AI | Groq API (LLaMA 3.1 8B Instant) |
| PWA | Service Worker + Web App Manifest |

## 🚀 Deployment

No build step required.

### Cloudflare Pages (recommended)
1. Go to dash.cloudflare.com → Workers & Pages → Create deployment
2. Upload the uniflow-pwa folder
3. Done

### GitHub Pages
1. Push files to a public repository
2. Settings → Pages → Deploy from branch → main → / (root)

## ⚙️ Configuration

Set your API key in index.html before deploying:

```js
const GROQ_KEY = 'your-groq-key'; // get free at console.groq.com
```

Add your deployment domain to Firebase Auth authorized domains.

### Firebase Storage Rules
```
rules_version = '2';
service firebase.storage {
  match /b/{bucket}/o {
    match /users/{userId}/docs/{allPaths=**} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

## 📁 Structure

```
uniflow-pwa/
├── index.html        <- Entire app (~2400 lines)
├── manifest.json     <- PWA config
├── sw.js             <- Service Worker
├── icon-192.png      <- App icon
├── icon-512.png      <- App icon large
├── icon-infinity.png <- Logo
├── flow-mascot.png   <- Flow AI mascot
├── _redirects        <- SPA routing
├── _routes.json      <- Cloudflare routing
└── README.md
```

## 🔒 Security

API keys are client-side (fine for personal use). For large-scale production, proxy via Cloudflare Workers.

## 📄 License

MIT

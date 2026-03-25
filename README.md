# Moveup — Full-Stack CRUD App

A responsive, full-featured personal data manager built with vanilla HTML, CSS, and JavaScript. No frameworks, no dependencies, no build step — just open `index.html` in a browser.

![Nexus Preview](docs/preview.png)

---

## ✨ Features

| Feature | Details |
|---|---|
| **Authentication** | Register & login with email/password, session persists on refresh |
| **Create** | Modal form with title, category, and description |
| **Read** | Card grid with live search + category filters |
| **Update** | Edit modal pre-populated with existing data |
| **Delete** | Confirmation dialog before permanent removal |
| **Stats** | Live record counts per category |
| **Toasts** | Success/error feedback on every action |
| **Responsive** | Fully works on mobile, tablet, and desktop |
| **Accessible** | ARIA roles, labels, keyboard navigation |

---

## 🚀 Getting Started

### Option 1 — Open directly
```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/nexus-crud.git

# Open in browser
open frontend/index.html
```

### Option 2 — Serve locally
```bash
# Using Python
cd frontend
python3 -m http.server 8080

# Using Node.js (npx)
npx serve frontend

# Then visit: http://localhost:8080
```

---

## 📁 Project Structure

```
moveup-crud/
├── frontend/
│   ├── index.html          ← App entry point
│   ├── css/
│   │   ├── reset.css       ← Box-model reset
│   │   ├── variables.css   ← Design tokens & CSS custom properties
│   │   ├── auth.css        ← Login & Register screens
│   │   ├── layout.css      ← Topbar, main, stats, toolbar, grid
│   │   ├── components.css  ← Buttons, fields, cards, toast, animations
│   │   ├── modals.css      ← Dialog overlays
│   │   └── responsive.css  ← Mobile & tablet breakpoints
│   └── js/
│       ├── db.js           ← Database layer (localStorage)
│       ├── auth.js         ← Authentication API
│       ├── api.js          ← Items CRUD API
│       ├── ui.js           ← DOM rendering & UI helpers
│       └── app.js          ← App controller & event wiring
├── docs/
│   └── ARCHITECTURE.md     ← System design notes
├── .gitignore
└── README.md
```

---

## 🏗️ Architecture

The app follows a **clean 3-layer architecture** that mirrors a real full-stack application:

```
┌─────────────────────────────────────────┐
│              UI LAYER (ui.js)           │  ← DOM rendering, templates
├─────────────────────────────────────────┤
│     BUSINESS LOGIC (auth.js, api.js)    │  ← Auth, CRUD operations
├─────────────────────────────────────────┤
│          DATABASE LAYER (db.js)         │  ← localStorage persistence
└─────────────────────────────────────────┘
```

- **`db.js`** — Wraps `localStorage` reads/writes. Replace with `fetch()` calls to swap in a real backend.
- **`auth.js`** — Registration, login, logout, session management.
- **`api.js`** — Full CRUD with validation, unique IDs, timestamps.
- **`ui.js`** — All DOM rendering. XSS-safe via `escHtml()`. Exports `UI` namespace.
- **`app.js`** — Wires all layers together. Manages app state, event listeners, routing.

---

## ⌨️ Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| `Escape` | Close any open modal |
| `Ctrl / ⌘ + Enter` | Save item in modal |
| `Ctrl / ⌘ + K` | Focus the search bar |
| `Enter` | Submit login or register form |

---

## 🗂️ Data Model

### User
```json
{
  "id":        "lx3k9a2b...",
  "name":      "Jane Smith",
  "email":     "jane@example.com",
  "password":  "hashed_string",
  "createdAt": "2025-01-15T10:30:00.000Z"
}
```

### Record (Item)
```json
{
  "id":          "m7p2q8r...",
  "title":       "Q4 Report",
  "description": "Annual performance summary",
  "category":    "Work",
  "createdAt":   "2025-01-15T10:31:00.000Z",
  "updatedAt":   "2025-01-15T11:00:00.000Z"
}
```

### Categories
`Work` · `Personal` · `Idea` · `Urgent` · `Archive`

---

## 🔐 Security Notes

- Passwords are hashed (simple JS hash — suitable for demo only)
- All rendered content is HTML-escaped to prevent XSS
- Sessions are stored in `localStorage` (not cookies)
- For production: use `bcrypt` on a real server, HTTPS, and JWT tokens

---

## 🌐 Deploy to GitHub Pages

```bash
# In your repo settings → Pages → Source: Deploy from branch → main → /frontend
# Your app will be live at: https://YOUR_USERNAME.github.io/nexus-crud/
```

Or use the CLI:
```bash
gh repo create nexus-crud --public
git init && git add . && git commit -m "Initial commit"
git push -u origin main
```

---

## 📄 License

MIT — free to use, modify, and distribute.

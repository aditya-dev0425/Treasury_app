# Treasury — Project Context & AI Guidelines

## 1. Project Overview
**Treasury** is a campus lost-and-found web app where students can post photos and details of found items, browse/search lost belongings, and contact the uploader to recover them.

## 2. MVP Features
- **Feed / Browse Page:** View all posted found items as cards (photo, item title, location found, date, status).
- **Search & Filter:** Filter items by category (ID Card, Electronics, Keys, Bottle, Other) or search by keyword.
- **Post Found Item:** Form to upload an item photo, title, description, location found, and contact info (phone/email/Instagram).
- **Item Detail & Contact:** Clicking an item shows full details and a clear way to contact the finder.
- **Mark as Claimed:** Ability to mark an item as returned/claimed.

## 3. Tech Stack
*(Update this section before coding so both AIs generate matching code)*
- **Frontend:** [e.g., HTML, CSS, Vanilla JS / React + Tailwind]
- **Backend:** [e.g., Node.js + Express / Firebase / Supabase]
- **Database & Image Storage:** [e.g., MongoDB + Cloudinary / Supabase / Local JSON for MVP]

## 4. Folder Structure
```text
Treasury_app/
├── CONTEXT.md          # Shared project rules (this file)
├── README.md
├── frontend/           # (or public/ / src/)
│   ├── index.html      # Main feed page
│   ├── post.html       # Upload found-item page
│   ├── item.html       # Single item detail page
│   ├── css/
│   │   └── style.css   # Shared global styles & variables
│   └── js/
│       ├── feed.js
│       ├── post.js
│       └── item.js
└── backend/            # (if using Node/Express)
    ├── server.js
    └── routes/
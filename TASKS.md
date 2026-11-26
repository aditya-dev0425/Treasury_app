# Treasury — Task Breakdown & Roadmap

> **Team Split**
> - **Person A (Frontend & UI):** `[Name]` — owns `/client`
> - **Person B (Backend & Infra):** `[Name]` — owns `/server`

---

## Phase 0: Shared Kickoff (Do Together)
- [ ] Agree on the tech stack (React + Vite + Tailwind, Node + Express, MongoDB Atlas, Cloudinary)
- [ ] Finalize API routes and JSON request/response formats in `CONTEXT.md`
- [ ] Set up root `.gitignore` (ignore `node_modules/`, `.env`, `dist/`)
- [ ] Create `/client` and `/server` folders on `main` and push initial structure

---

## Phase 1: Project Setup

### Person A — Frontend (`/client`)
- [ ] Initialize React + Vite project inside `/client`
- [ ] Install and configure Tailwind CSS
- [ ] Install `react-router-dom` and `axios`
- [ ] Set up basic routes (`/`, `/login`, `/register`, `/post`, `/item/:id`, `/profile`)
- [ ] Build shared layout: Navbar (responsive) + Footer

### Person B — Backend (`/server`)
- [ ] Initialize Node.js + Express project inside `/server`
- [ ] Install core dependencies (`express`, `mongoose`, `cors`, `dotenv`, `bcryptjs`, `jsonwebtoken`, `multer`, `cloudinary`)
- [ ] Set up MongoDB Atlas cluster and connect via `MONGO_URI` in `.env`
- [ ] Configure CORS, JSON parsing, and a `/api/health` test route
- [ ] Set up folder structure (`models/`, `routes/`, `controllers/`, `middleware/`)

---

## Phase 2: Authentication

### Person A — Frontend (`/client`)
- [ ] Build Register page (name, college email, contact info, password)
- [ ] Build Login page
- [ ] Create AuthContext to store JWT token and logged-in user state
- [ ] Create `ProtectedRoute` wrapper for `/post` and `/profile`
- [ ] Update Navbar to show Login/Register vs. Profile/Logout dynamically

### Person B — Backend (`/server`)
- [ ] Create `User` Mongoose schema (`name`, `email`, `passwordHash`, `contactInfo`, `createdAt`)
- [ ] Build `POST /api/auth/register` (hash password with `bcrypt`, return JWT)
- [ ] Build `POST /api/auth/login` (verify credentials, return JWT)
- [ ] Build `authMiddleware` to verify JWT from `Authorization` header
- [ ] Build `GET /api/auth/me` (protected route returning current user)

---

## Phase 3: Core Lost & Found Features

### Person A — Frontend (`/client`)
- [ ] Build `ItemCard` component (photo, title, Lost/Found badge, location, date, status)
- [ ] Build Home Feed (`/`) with grid layout
- [ ] Add Search bar + Category filter + Lost/Found & Status filters
- [ ] Build Post Item page (`/post`) with form fields and live image preview
- [ ] Build Item Detail page (`/item/:id`) showing full description + uploader contact button
- [ ] Add "Mark as Returned" and "Delete" buttons on items owned by the logged-in user

### Person B — Backend (`/server`)
- [ ] Configure Cloudinary SDK and `multer` upload middleware
- [ ] Create `Item` Mongoose schema (`title`, `description`, `type`, `category`, `location`, `date`, `imageUrl`, `status`, `postedBy`, `createdAt`)
- [ ] Build `POST /api/items` (protected: upload image to Cloudinary + save item)
- [ ] Build `GET /api/items` (support `?search=`, `?category=`, `?type=`, `?status=` filters)
- [ ] Build `GET /api/items/:id` (populate `postedBy` name and contact info)
- [ ] Build `PATCH /api/items/:id/status` (protected, owner-only: mark as `"returned"`)
- [ ] Build `DELETE /api/items/:id` (protected, owner-only: delete item)

---

## Phase 4: Dashboard, Polish & Deployment

### Person A — Frontend (`/client`)
- [ ] Build User Profile / Dashboard (`/profile`) listing the user's own posts
- [ ] Add loading spinners, empty states, and error/success toast notifications
- [ ] Test and fix mobile responsiveness across all pages
- [ ] Deploy `/client` to Vercel and set `VITE_API_URL` environment variable

### Person B — Backend (`/server`)
- [ ] Add input validation and centralized error-handling middleware
- [ ] Verify owner-only checks on update/delete routes
- [ ] Seed sample campus items for testing
- [ ] Deploy `/server` to Render/Railway and configure production `.env` variables

---

## Shared Integration & Launch
- [ ] Connect deployed frontend to deployed backend and verify CORS
- [ ] End-to-end test: Register -> Login -> Post with Photo -> Search/Filter -> Mark Returned -> Delete
- [ ] Update `README.md` with live link and screenshots

---

## Git Workflow Rules
1. Never push directly to `main`.
2. Create a branch per feature: `git checkout -b feat/login-page` or `feat/items-api`.
3. Pull latest `main` before opening a Pull Request: `git pull origin main`.
4. Review and merge PRs on GitHub, then check off completed boxes in `TASKS.md`.
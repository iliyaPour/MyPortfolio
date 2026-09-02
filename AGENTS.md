# AGENTS.md

## Project

Vue 3 portfolio/resume site. Vite 8, Tailwind CSS 4, Font Awesome.

## Commands

```sh
npm run dev        # dev server
npm run build      # production build
npm run format     # prettier on src/
```

No lint, typecheck, or test suite configured.

## Key Details

- **Node**: `^22.18.0 || >=24.12.0` (see `package.json` engines)
- **Tailwind v4**: Uses `@tailwindcss/vite` plugin (not PostCSS). CSS entry is `src/assets/styles/main.css`.
- **Font Awesome**: Icons imported manually in `src/main.js`. To add icons, import from `@fortawesome/free-solid-svg-icons` or `@fortawesome/free-brands-svg-icons` and register via `library.add()`.
- **Prettier**: No semicolons, single quotes, 100 print width. Run with `--experimental-cli` flag (already in script).
- **`@` alias**: Maps to `src/` (configured in `vite.config.js` and `jsconfig.json`).
- **Component structure**: `src/components/layout/` (Navbar, Footer), `src/components/sections/`, `src/components/ui/`.
- **Data**: Resume content lives in `src/data/resume.js`.

---

## Backend (Laravel + Breeze)

Located in `backend/`. Laravel 13 with Breeze API scaffolding (Sanctum).

### Backend Commands

```sh
cd backend
php artisan serve          # API server at http://localhost:8000
php artisan migrate        # run migrations
php artisan make:model     # create model
php artisan make:controller # create controller
```

### API Endpoints (Breeze)

- `POST /api/register` - Register
- `POST /api/login` - Login
- `POST /api/logout` - Logout (auth)
- `GET /api/user` - Get user (auth)

### Database

SQLite at `backend/database/database.sqlite`. Ignore in git.

### CORS

Allows `http://localhost:5173` (Vite dev server). Config in `backend/config/cors.php`.

### Sanctum

Token-based auth for SPA. Config in `backend/config/sanctum.php`.

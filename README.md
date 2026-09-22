# Training Tracker

A personal weekly strength/hypertrophy training tracker with multi-user support.

## Stack
- **Frontend**: single-page HTML/CSS/vanilla JS (no build step)
- **Auth**: Supabase magic-link email sign-in
- **Database**: Supabase Postgres (`training_checks` table, row-level security enabled — each user only sees their own data)
- **Hosting**: Netlify (site: `training-tracker-uzx`)

## Structure
- `index.html` — the entire app (UI, styling, and Supabase client logic)

## Local development
Just open `index.html` in a browser, or serve it with any static file server:

```bash
python3 -m http.server 8000
```

## Deployment
Connected to Netlify for hosting. Pushing to `main` can be wired to auto-deploy once the Netlify site is linked to this repo.

## Database schema
See the `training_checks` table in the linked Supabase project:
- `user_id` (references `auth.users`)
- `exercise_key` (identifies which exercise/day/set)
- `done` (boolean)
- `updated_at`

Row-level security policies restrict all reads/writes to the authenticated user's own rows.

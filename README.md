# EventFlow — Event Registration Tracker

A local-first React/Vite MVP for tracking hackathons, competitions, internships and event deadlines.

## Run
Requires Node.js 22+.
```bash
npm install
npm run dev
```
Build with `npm run build`.

## Included now
- Dashboard statistics
- Add/delete registrations
- Event name, organizer, category, URL, status, deadline, dates, priority and notes
- Upcoming deadline calculation
- Event list/search
- Timeline preview
- Calendar-style deadline list
- Local persistence with localStorage
- JSON backup/import
- Responsive UI

## Production upgrade
The UI is intentionally usable without credentials. For multi-device accounts, connect Supabase using `VITE_SUPABASE_URL` and `VITE_SUPABASE_PUBLISHABLE_KEY`, add Auth, Postgres tables and RLS ownership policies. Explicitly grant only required Data API operations to `authenticated`; new Supabase projects may not auto-expose new tables. Never expose a service-role/secret key in Vite client code.

Recommended tables: `events`, `milestones`, `reminders`, `attachments`, each owned by `user_id`. Enable RLS on every exposed table and enforce `auth.uid() = user_id` for select/insert/update/delete.

Google Calendar and dependable scheduled reminders require authenticated server-side/OAuth handling; keep provider secrets outside the browser. Add these after the core tracker is connected to Supabase.

## Deploy
Push to GitHub and import the repo into Vercel. Vite builds with `npm run build` and outputs `dist`.

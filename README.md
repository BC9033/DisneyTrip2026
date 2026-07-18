# The Cohen Family Disney World Adventure 🏰

An interactive, mobile-friendly itinerary for our Walt Disney World trip, **September 18–25, 2026**.

**Live site:** https://bc9033.github.io/DisneyTrip2026/ (repo `bc9033/DisneyTrip2026`, path case-sensitive)

---

## What's inside `index.html`

A single self-contained web page (no build step, no dependencies) with five tabs:

- **Overview** — dates, travelers, resorts, flights, transport, live countdowns, and a week-at-a-glance grid
- **Daily** — all 8 days with collapsible hour-by-hour timelines
- **Dining** — all 14 reservations with tier ratings, times, and locations
- **Rider Swap** — height minimums by park for Casper (~44") and Evie (~40"), heights as of 2026-06-23; exact-threshold rides are measure-day-of
- **Booking** — critical-date timeline plus the July 22 reservation checklist (your check-offs save in the browser)

### Links
- 📍 **Map** buttons open **Google Maps** (and the Maps app on a phone).
- 🏰 **Disney** buttons open the official Walt Disney World page, which launches the **My Disney Experience** app on a phone that has it installed.

---

## Deploy to GitHub Pages

**Option A — web upload (no command line)**
1. Create a new repository on GitHub (e.g. `disney-2026`). Make it **Public**.
2. Click **Add file → Upload files**, drag in `index.html` (and `README.md`, `.nojekyll`), and commit.
3. Go to **Settings → Pages**. Under *Build and deployment*, set **Source = Deploy from a branch**, **Branch = `main` / `root`**, and **Save**.
4. Wait ~1 minute. Your site is live at `https://<your-username>.github.io/<repo-name>/`.

**Option B — command line**
```bash
cd "Interactive Site"
git init && git add . && git commit -m "Disney 2026 itinerary site"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
# then enable Pages under Settings → Pages (branch: main / root)
```

---

## Updating the itinerary
Edit `index.html` directly (the old generator script is retired and must not be re-run; it predates the June 2026 redesign and would overwrite it). The booking checklist state lives in your browser's local storage, so it persists across visits on the same device. Keep exactly one `index.html` in this folder; stray copies invite editing the wrong file.

> Always re-verify park hours, show times, Extended Evening Hours, and reservation details in the My Disney Experience app ~30 days out — Disney's calendar can shift.

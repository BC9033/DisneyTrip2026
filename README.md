# The Cohen Family Disney World Adventure

An interactive, mobile-friendly itinerary for our Walt Disney World trip, **September 18 to 25, 2026**.

Working set **V10.6** (2026-09-04) — same plan, same facts, new scroll behaviour. V10 recorded the
reservation confirmation numbers; two Wednesday 9/23 slots remain open.

**Live site:** https://bc9033.github.io/DisneyTrip2026/ (repo `bc9033/DisneyTrip2026`, path case-sensitive)

---

**Phone booking console:** `console.html` is the standalone booking tracker (same one that lives as a desktop artifact). After upload it is at `https://bc9033.github.io/DisneyTrip2026/console.html`; open it on a phone and use Share, then Add to Home Screen. Check-offs save per device. It is linked from the site footer.

## What's inside `index.html`

A single self-contained web page (no build step, no dependencies, Google Fonts only, runs from `file://`)
with four tabs. It leads with the trip rather than with booking, and everything already booked has been
retired from the front page.

- **Overview** — a clock-aware hero countdown, a Now/Next strip, the week at a glance, trip particulars,
  what is still to do, and a packing checklist
- **Days** — one day at a time, chosen by calendar date (Fri 18 through Fri 25), with the full
  hour-by-hour schedule
- **Dining** — every reservation with time, location and confirmation number. Tap the restaurant name
  to open its official Disney page, which launches My Disney Experience on a phone that has it. As of
  the 2026-09-04 audit: 12 confirmed, plus the Four Seasons brunch confirmed hotel-direct; only Hollywood &
  Vine (Wed 9/23) is still OPEN. Sci-Fi Dine-In was booked on Ashley's account, so its number is pending
- **Rider Swap** — height minimums by park for Casper (~44") and Evie (~40"), heights as of 2026-06-23;
  exact-threshold rides are measure-day-of

### What the page does on its own
- **Hero countdown** reads the clock: days until wheels up before the trip, "Day N of eight" during it,
  and a closing card afterwards.
- **Now / Next** shows the next hard deadline before the trip and the current and next scheduled block
  during it. It refreshes every 60 seconds.
- **Still To Do** retires each item once its moment passes, and the whole section disappears when the
  list is empty. Next hard date: Lightning Lane Multi Pass, Sun 9/13 at 7:00 AM ET (6:00 AM CT).
- **The Checklist** saves to this browser under `cohen-disney-2026-packing`. The V10 booking-checklist
  key `cohen-disney-2026-booking` is preserved and never touched.
- **Print keepsake** (footer) prints all four tabs and all eight days on a white ground, without the
  navigation, day selector or checklist.
- On a phone the week becomes a tap-to-open accordion; on a wide screen a section rail tracks your
  position down the Overview, with a progress line that fills as you go.

### Motion
The Overview is scroll-aware. The hero settles in on load and the countdown numeral counts up.

**Nothing fades on scroll.** As you scroll the Overview, the hero *recedes* instead: the scene is four
stacked layers that lag the scroll by different amounts — distant hills 0.34, mid bank 0.24, castle
0.16, near bank 0.05, with the hero copy at 0.10 — so the bands separate with depth and sink out of
the bottom of their frame. Every element holds full opacity throughout. The count still hands off to a
small "15 days to go" mark in the top bar so it is never lost, and the bar itself condenses.

**Day schedules carry a timeline.** A thread runs down the schedule gutter with a dot for each block,
and the block at the reading line is picked out with a soft wash. Nothing else dims - every block stays
fully legible. The thread and dots are pure CSS
pseudo-elements, so no schedule row carries extra markup. Princess Day (Thu 9/24) draws in rose,
matching how that day is coloured everywhere else on the site.

**The "Up now" bar is a day-of instrument.** It appears only when you are actually living the day on
screen — Days tab open, today's date matching the day being viewed, page scrolled past the top, and
the day's first block already passed. It then follows the *clock*, not your scrolling, naming the
block happening right now from the schedule's own timestamps and refreshing every 60 seconds. So it
is invisible before 9/18 by design; append `?upnow=preview` to the URL to force it on for a look.

**Each panel settles once, then stops.** Rows no longer appear as you scroll into them — that made the
page feel like it was still loading while you read it. Instead a panel plays one orchestrated entrance
when you open it (staggered 26ms per row, capped at 620ms) and is then finished moving. Switching tab
or day replays that panel's entrance. Nothing at all is scroll-triggered.

Only elements actually on screen animate, so a block hidden by a breakpoint — the phone week at desktop
width, or the desktop week on a phone — is never left mid-animation.

All of it is presentation only. With `prefers-reduced-motion: reduce`, with JavaScript off, or in the
print view, every element is simply visible with no transforms — nothing depends on motion to be read.

### Readability
Set for reading at arm's length. Body text is 18px, headings and labels are larger and heavier, and
every text colour clears the WCAG AA 4.5:1 contrast bar against the cream ground — the pale golds are
kept for hairlines and borders only, with darker golds carrying the words. Verified by an automated
sweep of every rendered text node on all four tabs.

### Links
- **Map** links open **Google Maps** (and the Maps app on a phone).
- **Disney** links open the official Walt Disney World page, which launches the **My Disney Experience**
  app on a phone that has it installed.

---

## Deploy to GitHub Pages

**Option A — web upload (no command line)**
1. Open the repository on GitHub (`bc9033/DisneyTrip2026`). It must be **Public**.
2. Click **Add file → Upload files**, drag in `index.html` and `console.html` (and `README.md`, `.nojekyll`), and commit.
3. Go to **Settings → Pages**. Under *Build and deployment*, set **Source = Deploy from a branch**, **Branch = `main` / `root`**, and **Save**.
4. Wait ~1 minute. The site is live at `https://bc9033.github.io/DisneyTrip2026/`.

**Option B — command line**
```bash
cd "Interactive Site"
git init && git add . && git commit -m "Disney 2026 itinerary site V10.6"
git branch -M main
git remote add origin https://github.com/bc9033/DisneyTrip2026.git
git push -u origin main
# then enable Pages under Settings → Pages (branch: main / root)
```

---

## Updating the itinerary
Edit `index.html` directly. The old site generator is retired and must not be re-run; it predates the
June 2026 redesign and would overwrite it. The build script `build/build_site.py` produced the V10
layout and no longer matches this file — treat it as historical. Keep exactly one `index.html` in this
folder; stray copies invite editing the wrong file.

Checklist state lives in your browser's local storage, so it persists across visits on the same device.

> Always re-verify park hours, show times, Extended Evening Hours, and reservation details in the
> My Disney Experience app ~30 days out — Disney's calendar can shift.

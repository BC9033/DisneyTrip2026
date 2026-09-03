The Cohen Family Disney World Adventure
An interactive, mobile-friendly itinerary for our Walt Disney World trip, September 18 to 25, 2026.

Working set V10.1 (2026-09-03) — same plan, same facts, redesigned presentation. V10 recorded the reservation confirmation numbers; two Wednesday 9/23 slots remain open.

Live site: https://bc9033.github.io/DisneyTrip2026/ (repo bc9033/DisneyTrip2026, path case-sensitive)

Phone booking console: console.html is the standalone booking tracker (same one that lives as a desktop artifact). After upload it is at https://bc9033.github.io/DisneyTrip2026/console.html; open it on a phone and use Share, then Add to Home Screen. Check-offs save per device. It is linked from the site footer.

What's inside index.html
A single self-contained web page (no build step, no dependencies, Google Fonts only, runs from file://) with four tabs. It leads with the trip rather than with booking, and everything already booked has been retired from the front page.

Overview — a clock-aware hero countdown, a Now/Next strip, the week at a glance, trip particulars, what is still to do, and a packing checklist

Days — one day at a time, chosen from an eight-day selector, with the full hour-by-hour schedule

Dining — every reservation with tier, time, location and confirmation number. As of the 2026-09-03 audit: 11 confirmed, plus the Four Seasons brunch confirmed hotel-direct; Hollywood & Vine and Sci-Fi Dine-In (both Wed 9/23) are OPEN with no confirmation on file

Rider Swap — height minimums by park for Casper (~44") and Evie (~40"), heights as of 2026-06-23; exact-threshold rides are measure-day-of

What the page does on its own

Hero countdown reads the clock: days until wheels up before the trip, "Day N of eight" during it, and a closing card afterwards.

Now / Next shows the next hard deadline before the trip and the current and next scheduled block during it. It refreshes every 60 seconds.

Still To Do retires each item once its moment passes, and the whole section disappears when the list is empty. Next hard date: Lightning Lane Multi Pass, Sun 9/13 at 7:00 AM ET (6:00 AM CT).

The Checklist saves to this browser under cohen-disney-2026-packing. The V10 booking-checklist key cohen-disney-2026-booking is preserved and never touched.

Print keepsake (footer) prints all four tabs and all eight days on a white ground, without the navigation, day selector or checklist.

On a phone the week becomes a tap-to-open accordion; on a wide screen a section rail tracks your position down the Overview.

Links

Map links open Google Maps (and the Maps app on a phone).
Disney links open the official Walt Disney World page, which launches the My Disney Experience app on a phone that has it installed.
Deploy to GitHub Pages
Option A — web upload (no command line)

Open the repository on GitHub (bc9033/DisneyTrip2026). It must be Public.
Click Add file → Upload files, drag in index.html and console.html (and README.md, .nojekyll), and commit.
Go to Settings → Pages. Under Build and deployment, set Source = Deploy from a branch, Branch = main / root, and Save.
Wait ~1 minute. The site is live at https://bc9033.github.io/DisneyTrip2026/.
Option B — command line

cd "Interactive Site"
git init && git add . && git commit -m "Disney 2026 itinerary site V10.1"
git branch -M main
git remote add origin https://github.com/bc9033/DisneyTrip2026.git
git push -u origin main
# then enable Pages under Settings → Pages (branch: main / root)
Updating the itinerary
Edit index.html directly. The old site generator is retired and must not be re-run; it predates the June 2026 redesign and would overwrite it. The build script build/build_site.py produced the V10 layout and no longer matches this file — treat it as historical. Keep exactly one index.html in this folder; stray copies invite editing the wrong file.

Checklist state lives in your browser's local storage, so it persists across visits on the same device.

Always re-verify park hours, show times, Extended Evening Hours, and reservation details in the My Disney Experience app ~30 days out — Disney's calendar can shift.

# The Dogs Bollox — the consensus board

Third phone app alongside Sandstorm and The Holy Grail (plus Jacobs Ladder).

This is the FRESH install address (the original dgs-bolx address kept a
phantom install record on Dave's phone — Chrome kept saying "already
installed" for it. New path = no ghost).

What it does, every time it's opened:
1. Pulls the day's published picks live from all three apps (GitHub Pages data
   files are CORS `*`, so the phone does the join directly — no server needed):
   - Sandstorm: `jobsaboba.github.io/wonderland/data/<day>.json` — `races[].sel`
   - Holy Grail: `jobsaboba.github.io/holy-grail/data/<day>.json` — top-3 ranked runners
   - Jacobs Ladder: `jobsaboba.github.io/jacobs-ladder/data/<day>.json` — `finals`
2. Joins on normalised course | time | horse.
3. Medals the horses:
   - 🏆 **Gold cup** — picked by all three apps (even bigger chance of winning)
   - 🥈 **Silver** — two apps
   - Singles (one app only) are hidden — no medal, no bet.
4. Shows a WIN/PLACE/LOSE badge when one of the sources already knows the result.
5. Running bank: £10.00 start, 1% of the current bank staked on every medal
   (gold + silver), Sandstorm's hybrid terms — win pays the odds, place pays
   a quarter of the odds, a loss costs the stake, non-runners returned.
   Bets only settle when a result becomes known; recomputed from full
   published history each open (the fetch tail stops 7 days past the last
   medal day, so it stays light on the phone).

Days shown: the last four (the same window the launcher settles each morning).

## Publishing / changing

App shell repo: `jobsaboba/dgs-bollox` → GitHub Pages →
**https://jobsaboba.github.io/dgs-bollox/**
Edit `index.html` / `sw.js` / `manifest.webmanifest`, bump `APP_VER` in
index.html **and** the `CACHE` name in sw.js, commit + push — then
force-close and reopen the app on the phone.

# Football Camp

A 4-hour football crash course built around one skill: reading the field before the snap and predicting what's coming. It's a single static web page you can add to your phone's home screen. No build step and no server.

## What's inside

- **Stations 1–7** — personnel, the box, safeties and coverages (Cover 0–4), formations (including the T), the plays that matter plus your growing playbook, game situations, and pre-snap pictures to read. Every idea has a diagram, and every station ends with a quick quiz.
- **Station 8, the drill** — pause a game before each snap, log the game clock, yard line, what you see and your run/pass call (plus an optional bonus: name the exact play), then log what happened. You get accuracy by game and quarter against the "always pass" benchmark.
- **Game reviews** — the morning after a game you logged is final, each snap is matched to the real play, graded, and corrected where you logged something wrong. Plays you haven't learned yet get an explanation and diagram, and are added to your playbook.

## Where your data lives

- **Drill (Station 8), game reviews and playbook** → `foolserrandsf/football-film-room`, branch `data` (`data/games/`, `data/reviews/`, `data/plays/`). This is the same place the standalone Film Room app reads and writes, so a game logged in either app shows up in both, and the morning game review writes there.
- **Camp's quiz answers, snap-reading answers and station checkmarks** → this repo, branch `data` (`data/progress.json`).

Camp never edits football-film-room's `main` branch or its `data/progress.json` (that file belongs to the standalone app).

## Syncing (once per device)

Each device needs a sync key that can write to **both** repos:

1. Go to **github.com/settings/personal-access-tokens/new**.
2. Name it "Football Camp" and pick an expiration date.
3. **Repository access:** Only select repositories → `football-camp` and `football-film-room`.
4. **Permissions:** Repository permissions → **Contents: Read and write**.
5. Generate it, copy it, and paste it in the app under **Station 8 → Sync settings**.

Already saved a key that only covers `football-camp`? Don't make a new one: on GitHub, open Settings → Developer settings → Fine-grained tokens, open the key, add `football-film-room` under Repository access, and save. The key itself doesn't change, so devices that already have it start syncing the next time the app opens.

The key is stored only in that device's browser. Without a key the app still works and shows your games and reviews, but new snaps stay on that device. Both repos are public, so anyone can read your logged snaps; nobody can change them without a key.

## Hosting on GitHub Pages

Settings → Pages → Build and deployment → Source: **Deploy from a branch**, branch `main`, folder `/ (root)`. The app is then at `https://<username>.github.io/football-camp/`. Data commits go to `data` branches, so they never trigger a Pages rebuild.

## Updating the app

Edit `index.html`, then bump `VERSION` in `sw.js` so installed copies pick up the change.

## Run it locally

```sh
python3 -m http.server 8000
```

Then open http://localhost:8000. Locally it syncs with the same two repos.

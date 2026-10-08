# Football Film Room

A 4-hour football crash course built around one skill: reading the field before the snap and predicting what's coming. It's a single static web page you can add to your phone's home screen. No build step and no server.

## What's inside

- **Stations 1–7** — personnel, the box, safeties and coverages (Cover 0–4), formations (including the T), the plays that matter plus your growing playbook, game situations, and pre-snap pictures to read. Every idea has a diagram, and every station ends with a quick quiz.
- **Station 8, the drill** — pause a game before each snap, log the game clock, yard line, what you see and your run/pass call (plus an optional bonus: name the exact play), then log what happened. You get accuracy by game and quarter against the "always pass" benchmark.
- **Game reviews** — the morning after a game you logged is final, each snap is matched to the real play, graded, and corrected where you logged something wrong. Plays you haven't learned yet get an explanation and diagram, and are added to your playbook.

## Syncing (once per device)

Your games, quiz answers, snap-reading answers and station checkmarks are saved as files in this repo on the `data` branch (`data/games/`, `data/progress.json`), so they're on every device and the morning review can read them. Other devices pick up changes when the app opens or you switch back to it. Each device needs a sync key:

1. Go to **github.com/settings/personal-access-tokens/new**.
2. Name it "Film Room" and pick an expiration date.
3. **Repository access:** Only select repositories → `football-camp`.
4. **Permissions:** Repository permissions → **Contents: Read and write**.
5. Generate it, copy it, and paste it in the app under **Station 8 → Sync settings**.

The key is stored only in that device's browser. Without a key the app still works and still shows your reviews, but new snaps stay on that device.

The repo is public, so your logged snaps are readable by anyone. Nobody can change them without a key.

## Hosting on GitHub Pages

Settings → Pages → Build and deployment → Source: **Deploy from a branch**, branch `main`, folder `/ (root)`. The app is then at `https://<username>.github.io/football-camp/`. Data commits go to the `data` branch, so they never trigger a Pages rebuild.

## Updating the app

Edit `index.html`, then bump `VERSION` in `sw.js` so installed copies pick up the change.

## Run it locally

```sh
python3 -m http.server 8000
```

Then open http://localhost:8000. Locally it syncs with `foolserrandsf/football-camp`.

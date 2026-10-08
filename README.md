# Film Room data

This branch holds the app's saved data. The app on `main` reads and writes it; nothing here is served as a web page.

- `data/games/<id>.json` — one file per game you log in the drill: `{name, created, snaps: [...]}`
- `data/reviews/<id>.json` — the game review written the morning after a game is final (same id as the game)
- `data/plays/<slug>.json` — play types added to your playbook beyond the core seven

Each snap: `t` (when you logged it, also its id), `q` quarter, `clock` game clock, `spot` yard line, `sit` down & distance, `pers` personnel, `box` box count, `saf` safeties, `pred` your call, `act` what happened, `play` your bonus call.

# Changelog

What changed, **in the words of someone who plays the game**. "Map tier is ticked automatically",
never "refactored initModFilters". Three of these lines land on the update prompt inside the app,
all of them land in the GitHub release, and both come from this one file — so it is not a
courtesy, it is a shipping artefact (`scripts/release-notes.mjs` reads it).

Rules for writing an entry:

- **The top section must be the version in `package.json`.** The release build refuses to publish
  otherwise, because the updater matches releases by version.
- Newest first, `## <version> — <YYYY-MM-DD>`.
- Lead with the line a player would care about most; only the first three reach the in-app prompt.
- Say what is different for them, not what moved in the code. If a change has no player-visible
  effect, it does not need a line.

<!-- minimum_supported: 0.0.0 -->

The line above is an **emergency lever**, not a routine field. Set it to a version number and
every older build stops offering to update and starts saying, in words, that it no longer works —
which is what we want the day a Path of Exile trade-API change breaks old builds mid-league.
Raising it strands everyone below it, so it is edited deliberately and never as housekeeping.

---

## 0.36.1 — 2026-09-06

- The league list works again for Path of Exile 2. It was arriving from the trade site all along
  and being thrown away before it reached you, which is why the league had to be typed by hand
- Because of that, the "a newer league has started" warning could never fire for PoE2 — it had no
  list to compare against. It can now

## 0.36.0 — 2026-09-06

- **Restart now** means restart now. It no longer refuses because Path of Exile is open, and it no
  longer sits there for several seconds before doing anything — it says *"Installing…"* the moment
  you press it and the app comes back on its own
- Opening Settings checks for a new version by itself, so you are not pressing a button to find out
- The update offer now appears in Settings and on the tray icon menu too, not only on the
  price-check window

## 0.35.2 — 2026-09-06

- Settings now has the **Restart now** button next to the message that tells you an update is
  waiting — before, the only button lived on the price-check window, so it was possible to have a
  downloaded update and nowhere to install it from
- Right-clicking the tray icon offers the same thing

## 0.35.1 — 2026-09-06

- If you are reading this inside the app, it just updated itself — which is the entire point of
  this release
- Every download now carries a checksum, so you can check that the file you got is the file we
  built

## 0.35.0 — 2026-09-05

- The app now installs like a normal Windows program, and updates itself from then on
- It asks before restarting, and never restarts while Path of Exile is running
- If an update can't install itself, it tells you where to get it instead of failing quietly
- It now says so when you price-check a PoE1 item while it is set to PoE2, instead of quietly
  searching the wrong market
- Settings points out when a newer league has started, instead of leaving you pricing against
  last league's economy

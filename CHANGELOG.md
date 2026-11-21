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

## 0.57.2 — 2026-11-22

- Cluster jewels now search by what they actually are: their small-passive type (e.g. Brand Damage) and exact passive count. Ticking that line used to find nothing.
- Cluster jewels with notables no longer require the minor "also grant" bonuses, so more real comparables come back.
- Vaal skill gems (Vaal Arctic Armour, Vaal Venom Gyre…) are priced as the Vaal gem now, instead of as the plain version of the skill.

## 0.57.0 — 2026-11-19

- **Mercenary Warrants can be price-checked in PoE1.** Before, the check found nothing at all. It
  now finds warrants of the same build (a Reanimator against other Reanimators, Infamous ones apart),
  and the card shows the mercenary, its level and every skill with its supports.
- Level and skills cannot be searched on the trade site, and the card says so. Click the Build line
  to compare against every warrant instead.

## 0.56.11 — 2026-11-15

- **Mods GGG reworded for the new league are read again.** Item Rarity on rings and amulets now
  reads "+11% to Item Rarity", and the app did not recognise it, so you could not search by it.
  It — and about a thousand other mods the trade site now spells differently — can be ticked again.

## 0.56.10 — 2026-11-15

- **Transfigured gems are priced again in PoE1.** Checking a gem like Lacerate of Haemorrhage used
  to fail outright; it now finds the market for that exact transfigured version.

## 0.56.9 — 2026-11-15

- **A new league no longer breaks price checks.** When a league ends, the app now switches to the
  new one by itself the moment it starts — for PoE1 and PoE2 alike. Before, a PoE1 check right
  after a league launch failed with "Invalid query" until you changed the league by hand.

## 0.54.1 — 2026-09-12

- **My market's "under" and "cheaper" figures were too big, and are fixed.** A price of 40 against
  a market of 100 said "150% under" — it is 60% under. The "over" figures were always right.
- **A loose match no longer calls your price wrong on a small gap.** When only a loose set of
  look-alikes can be found, it now needs a much bigger difference before it says "overpriced" or
  "undercut". A gap it cannot call reads "loose match — use hotkey" instead of pretending the
  price is fair.

---

## 0.54.0 — 2026-09-12

- **Rare gear and jewels are priced on the stats that sell them.** The price check now picks your
  item's strongest stats for its slot — movement speed on boots, life and defences on gloves — and
  adds or swaps one at a time until 10 to 100 items like it remain. A line under the price says
  what it picked.
- **My market can judge most of your rares now.** Rows that said "too many look-alikes" get a real
  answer, because they are compared the same way.
- **Jewels are compared with jewels.** They used to be searched against every item that could roll
  the same stats.
- Your own ticks always win: change a filter and nothing re-picks behind your back.

---

## 0.53.2 — 2026-09-12

- **You can read the "What is wrong" column now.** It was cutting its own explanations off
  mid-word. The messages are shorter, the column gets the spare room, and pointing at one shows the
  full sentence.

---

## 0.53.1 — 2026-09-12

- **Fewer of your price checks get blocked by work you never asked for.** The trade site limits how
  many searches can come from your connection, and test copies of the app were quietly using up a
  big share of it — enough to leave you locked out for an hour mid-game. They no longer do.

---

## 0.53.0 — 2026-09-12

- **Your own listing no longer helps decide what your item is worth.** When you price-checked
  something you already have up for sale, your own asking price was counted as one of the
  comparable listings — so it partly voted for itself, and always voted "you're priced about
  right". On a thin market that is worth a lot: on one of your gloves it was the difference
  between 3 divine and 6. Your listing is still in the list, marked **you**, so you can see where
  you sit in the queue — it just doesn't count towards the number any more.

---

## 0.52.0 — 2026-09-12

- **My market remembers what you checked.** Reading your listings and price-checking them costs
  real requests, and switching to the Stash tab and back used to throw all of it away. Now it is
  still there — after a tab switch and after a restart — and it tells you how long ago it was read.
  Market prices are dropped once they are old enough to mislead rather than shown as if current.
- **The drawn tab and the list sit side by side.** Reading one no longer scrolls the other off the
  screen. The item pictures and the text are both a size up.
- **A new "check everything" button.** Prices every listing you have not checked yet, dearest
  first. It skips anything already priced, so pressing it twice costs nothing the second time, and
  it stops itself if Path of Exile starts throttling — what it already found is kept.
- **It no longer calls you overpriced when it cannot tell.** On an item whose look-alikes number in
  the thousands, the comparison was against the whole category rather than your item — which had it
  telling you a 3-divine pair of gloves was "120x over the market" while the price-check overlay,
  asked about the same gloves, said 2-3 divine. Those rows now say so plainly and point you at the
  hotkey. The one thing a crowd like that can still prove — that you are asking less than even the
  cheapest of them — is still reported.

---

## 0.51.0 — 2026-09-12

- **New: "My market" tells you which of your own prices are wrong.** It reads the items you have
  up for sale and flags the ones priced below the market, the ones somebody has undercut, and the
  ones that have been sitting unsold long enough that the price is stale. Open the Stash Tracker
  from the tray and pick the **My market** tab.
- **It draws your stash tab, so you can find the item.** Your listings appear laid out exactly as
  they sit in the tab, each one tinted by what is wrong with its price — so a warning ends at
  "it is that square" instead of sending you back into the game to hunt for it. Point at a square
  to find its row, or at a row to find its square.
- **It works in Path of Exile 2 as well as Path of Exile 1.** The Stash Tracker itself cannot run
  on PoE2 — the game gives us no way to read a stash — so on PoE2 that window used to be a dead
  end. Now it opens straight onto My market instead.
- **Reading your listings costs one request, however many you have.** The price, the stash tab and
  how long the price has been sitting there all come with it, so the "stale" warnings appear for
  free. Checking a listing against the live market is a separate button, and it starts with your
  most expensive items, because those are the ones where being wrong actually costs you.
- **Currency conversion in PoE2 is right now.** Prices you can compare at a glance even when one
  item is priced in chaos, the next in exalted and the next in divine — and the rate for divine
  comes from the in-game Currency Exchange rather than a third-party site that was reading it 45%
  too high.

## 0.50.0 — 2026-09-12

- **Price checks stop queueing behind themselves.** The app was pacing itself to a made-up speed —
  slower than the trade site actually allows, while still firing fast enough in bursts to earn a
  one-minute time-out. Checking two items in a row could leave the third waiting several seconds.
  It now follows the real limits the site reports on every reply.
- **It can no longer walk into an hour-long lockout without seeing it coming.** The trade site also
  caps searches over a three-hour window, and the app was completely blind to that one — it could
  only find out by being locked out. It now counts it, and picks up how much has already been used
  so a restart doesn't start over and blunder into the cap.

---

## 0.49.0 — 2026-09-12

- **Your login keeps itself topped up.** Alongside your account session the trade site issues a
  second pass that only lasts a day, and the app used to collect it once when you signed in and
  then let it go stale for good. It now quietly renews itself in the background — no window, no
  interruption, nothing for you to click.
- **Settings tells you where that pass stands.** A line under your account session says whether it
  is valid and until when. It had been expired for six weeks on a working install and there was no
  way to see that short of digging through files.
- **The login message says who you actually signed in as.** It used to claim a capability nobody
  had ever checked; now it just shows your account name.

---

## 0.48.0 — 2026-09-12

- **The Expedition panel tells you when it is still working.** If prices are being measured, gem
  rows now show a waiting marker and a small counter instead of sitting blank — an empty strip and
  a broken feature looked identical, and they are not the same thing.
- **Prices appear as they are measured, not all at the end.** A full measurement takes minutes; the
  gems already done now show up straight away instead of waiting for the last one.
- **When there are no prices at all, measuring starts almost immediately** rather than after the
  usual polite minute. That minute is for refreshing prices you can already see.

---

## 0.47.1 — 2026-09-12

- **The Expedition badges appear about twice as fast.** They were waiting for a second confirming
  look at the screen before showing anything, which bought nothing — the thing being recognised is
  the reward window's own frame, and nothing in the game world can imitate it.

---

## 0.47.0 — 2026-09-12

- **Expedition prices you were still seeing from before the fixes are now thrown away.** The gem
  prices were corrected twice today, but your machine kept using the table it had already saved —
  it was only hours old, so nothing thought to replace it. The app now notices when a saved table
  was worked out a different way and measures again instead of drawing badges from it.

---

## 0.46.3 — 2026-09-12

- **The stray scrollbar over the game is gone.** A grey scrollbar had been appearing at the bottom of
  the Expedition badge strip. It was ours — the little star on the best badge was poking a pixel
  outside its strip and that was enough to summon one.
- **The badges form a straight column now.** They were following the text the app reads, and that
  reading shifts by a few pixels depending on the letters in a row. They now sit on the reward
  list's own grid, which is what the eye expects.
- **The currency coins are readable.** The badge tile was shading towards its bottom corner, which
  is exactly where the coin sits — so the tile was hiding the one thing on it that needed to stand
  out. The shading is flipped and the coin has a pale disc behind it.

---

## 0.46.2 — 2026-09-12

- **The exchange price is a proper badge now, and says nothing else.** It used to be small, dim,
  and followed by an apology about a price the app cannot read. That number is roughly what the
  item is worth, so it is shown plainly; the only extra word is whether it is what you sell for or
  what it costs to buy.

---

## 0.46.1 — 2026-09-12

- Nothing you can see. Internal: a request that fails to reach the exchange no longer looks like an
  item having no market, so a connection problem can't be mistaken for a price of nothing.

---

## 0.46.0 — 2026-09-12

- **Expedition values are converted at the real in-game rate.** They used to go through poe.ninja,
  which prices a divine about a third too high because it reads asking prices. They now use the
  in-game Currency Exchange's own order book, and every tier was re-measured against it.
- **The badges line up with their rows again.** A long reward list used to pile the bottom few up
  at the end of the strip; a badge is now either in exactly the right place or not drawn at all.
- **The currency coins are brighter**, so they read on the pale tile instead of disappearing into it.

---

## 0.45.2 — 2026-09-12

- **It no longer says "no buyers" when there are plenty.** For currency and similar items the app
  can only see the selling half of the in-game exchange. It used to read that as nobody wanting to
  buy, which was wrong — the exchange had thousands waiting. It now says what it can see, that you
  can buy at this price, and admits the sale price is lower and not something it can read yet.

---

## 0.45.1 — 2026-09-12

- Nothing you can see: this release only fills in the notes for three earlier updates that shipped
  without them, and adds plumbing the next one needs.

---

## 0.45.0 — 2026-09-12

- **The Expedition badges show a value instead of a letter.** A tier letter needed decoding; a
  number does not. Each badge now shows roughly what that reward is worth, next to the game's own
  coin for divine, chaos or exalted — whichever the value actually lands in, so the number always
  stays short.
- **The badges no longer sit on the chat scrollbar.** The bottom of the strip used to reach over
  the little scroll control at the left edge of the chat window; it now stops just above it, and a
  badge on the very last row is nudged up rather than painted over it.

---

## 0.44.1 — 2026-09-12

- **The exchange price is one short line now, and it shows up straight away.** It used to be a
  paragraph of advice, and it only appeared on the second or third time you checked the same
  item. Now it is a single line, and a price you have already seen once comes back instantly.

---

## 0.44.0 — 2026-09-12

- **It tells you what you can SELL something for, not what it costs to buy.** You check prices on
  things you already own, so that is the number you want. Where nobody is standing by to buy —
  which is common — it says so plainly and tells you what sellers are asking instead, so you know
  what to undercut.
- **The currency converter was out by a third, and now is not.** It was using a website's estimate
  of what a divine is worth. It now uses the in-game Currency Exchange, where people actually
  trade, and says at the top which of the two it is using.
- The exchange price moved out of the header, where it was easy to miss, into the results area.

---

## 0.43.0 — 2026-09-12

- **Currency, runes, essences and the rest are priced at last.** Checking a Blazing Flux or an
  essence used to say "no listings found" — the market search simply does not carry that kind of
  item. The app now reads the in-game Currency Exchange, the same order book the NPC shows you,
  which covers about 800 of them.
- **It shows the price people are really trading at, not the cheapest listing.** The exchange is
  full of standing offers at silly prices that nobody ever takes; the app looks for where the
  orders actually pile up.
- **When a market cannot be read, it shows nothing rather than a guess.** Some order books are so
  lopsided that no honest number can be taken from them.

---

## 0.42.0 — 2026-09-12

- **The Expedition badges moved onto the book's spine.** They used to sit over the game world on the
  right, where they washed out against the scenery and you could barely see them. They are now small
  parchment tiles down the dark binding on the left, one per reward row, drawn to match the game's
  own art instead of the app's.
- **Gem prices were badly wrong and are fixed.** The values behind the tiers came from a bad
  calculation and were inflated by up to 27 times — some gems were even in the wrong order. Prices
  now come from the same engine your own price checks use, and only from **Instant Buyout**
  listings: if you can't buy it right now, it isn't a price. Two gems have no instant-buyout market
  at all and now show nothing rather than a number nobody can act on.
- **Gem rewards are read properly.** The reward list writes a gem three different ways — at level
  20, unspecified, or as a support — and they aren't the same reward. Before, every one of those
  rows was skipped entirely and showed no badge at all.
- Trade chat can no longer be mistaken for a reward when the reward list is scrolled down.

---

## 0.41.0 — 2026-09-12

- **Expedition rewards now come with a price.** Click a node, and when the Runeshape Combinations
  window opens each reward gets a small value badge — with a star on the best one in that list — so
  you are not picking what to blow up blind. Turn it on in Settings; it is off by default.
- **It stays quiet when it is not sure.** A reward it cannot identify exactly gets no badge at all,
  and neither do vague entries like "Unique Jewellery" that have no price until they drop. A blank
  line means "we don't know", never a guess.
- **Prices say how old they are.** Expedition gem values are measured from live listings in the
  background, at most once a day, and the panel always shows when that happened — league prices fall
  fast and a number with no date is one you should not trust.
- Settings now tells you whether a screen-watching feature can actually work on your monitor,
  instead of sitting there switched on and silently never firing.

---

## 0.40.2 — 2026-09-11

- **PoE2 skill gems can be searched by name now.** A gem's skill name is pinned (and shown selected),
  and its level comes ticked, so a "Leylines" search finds that gem instead of every active gem in
  the game. Before, the name couldn't be selected and the search had nothing to go on

## 0.40.1 — 2026-09-11

- **Sceptres with "Allies in your Presence" mods price correctly now.** An ally resistance buff was
  being counted as your own resistance and searched as a total the market doesn't recognise, so the
  whole sceptre came back with zero results. It's searched on its real mod now (that one alone went
  from 0 to a couple thousand comparables)

## 0.38.3 — 2026-09-10

- **"Reduced cost" mods find matches now.** A tablet's "costs 26% reduced Tribute" (and any similar
  "reduced …" line where less is better) was searched the wrong way round and came back with zero —
  not even the item itself. It's now searched as "at least this good", so it prices properly
- **No more false "wrong game" warning on Ritual tablets.** The "10 uses remaining" line was being
  mistaken for a modifier that only exists in PoE1, so a real PoE2 tablet was told to switch games.
  It's read as the charge counter it is now

## 0.38.2 — 2026-09-10

- **White (Normal) items are priced by their own base now.** A plain "Dueling Wand" is searched as
  a Dueling Wand instead of against every wand, and its base now shows up ticked as the "this base"
  line. Before, the base couldn't be selected and the price came from the whole category

## 0.38.1 — 2026-09-10

- **Sceptres are priced properly now.** A sceptre shows a **Spirit** line you can tick, and it's
  searched by the total Spirit it grants — the number the market actually shops on — so it finds
  real comparables instead of nothing. Before, it tried to match "% increased Spirit" and came back
  empty
- **Amulets that grant passive skills ("Allocates …") now find matches.** These were coming back
  with zero results; they're looked up correctly now, both allocations are searched at once instead
  of one being quietly dropped, and they no longer get greyed out as "no filter"

## 0.37.1 — 2026-09-06

- Fixed the app quietly losing its own log file. If it could not be opened at startup — a moment's
  bad luck was enough — the app kept working perfectly and never wrote another line, which is
  exactly when you most want it. It now retries, falls back to another file, and says which one

## 0.37.0 — 2026-09-06

- **Nothing is downloaded without asking you.** When a new version turns up you get a proper
  window with three answers: download and restart now, download only and install later, or not now
- The check still happens by itself when you open Settings — only the downloading and the
  installing are yours to decide
- Saying *not now* closes the window without throwing the update away; it stays in Settings and on
  the tray icon whenever you want it

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

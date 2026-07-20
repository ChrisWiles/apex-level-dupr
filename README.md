# Apex Level × DUPR

**A courtside report comparing [Apex Pickleball Clubs](https://apexpbclubs.podplay.app/) in-house skill levels (Cedar Park, TX) against players' real DUPR doubles ratings.**

**Live page:** https://chriswiles.github.io/apex-level-dupr/

![Apex level vs DUPR](data/preview.png)

## What it is

Every Apex player is placed at an in-house **level** (1B, 1+, 2, 2+, 3, 3+, 4, 4+, 5) — a coach's call, loosely aimed at DUPR. This page sets each player's Apex level against their **actual DUPR doubles rating** to see how the club's ladder lines up with the global scale.

**Scope:** this covers everyone who played an Apex session in the roughly two-week booking window **and** could be matched to a DUPR account near Austin — not the full club membership.

The page is a single self-contained `index.html` — all data is embedded inline, no server or build step. It has:

- A **reliability filter** (All rated / Reliable ≥50% / Established ≥70% / Maxed 100%) and an **Active (played within 1 year)** toggle that together live-recompute every chart and stat. Reliability is DUPR's own 0–100% confidence in a rating — it grows as a player logs more (and more recent) matches.
- **Correlation scatter** — DUPR against the Apex ladder, drawn as an **evenly spaced** progression of rungs (the "+" levels sit halfway between round levels), with the real trend line. Dots are shaded by DUPR reliability — pale for low-confidence ratings, deep blue for established ones.
- **Distribution by level** — box-and-whisker of the DUPR ratings inside each Apex level, showing how much real DUPR overlaps between neighboring levels.
- **Peer comparison** — every player listed against the **average DUPR at their own level** (not against the level number): all above-average players in one column, all below-average in the other, grouped by level.
- A **sortable data table** of every matched player.

Light/dark themes, hover tooltips, keyboard-focusable, works on mobile.

## What it found

- Apex level and real DUPR are **strongly correlated (r ≈ 0.87)** — the ladder ranks players well.
- One rung up the ladder (e.g. L3 → L3+) is worth about **+0.26 DUPR** on average.
- The level numbers themselves are a coach's ladder, not DUPR values, so the page doesn't compare a player to their level number — it compares them to the **other players at the same level**.

## Data & method

`data/player-level-vs-dupr.csv` is the full matched dataset, including the players who couldn't be matched; its `notes` column records how each name was matched to a DUPR account (Austin-metro disambiguation, name variants, tie-breaks) and the `confidence` column grades the match. `data/player-level-vs-dupr.md` is the longer write-up of the matching method and its hand-review passes.

- **Apex level** comes from the club's public PodPlay session catalog (each session carries a level band); a player's figure is the average of the sessions they attended.
- **DUPR rating** is a live lookup of each player's DUPR doubles rating, biased to the Cedar Park / Austin area for name disambiguation. Only **doubles** ratings are charted; singles and unrated (NR) accounts are set aside.

## Notes

Not affiliated with Apex Pickleball Clubs or DUPR. Apex level is a coach's placement, not a DUPR clone — a loose guide by design. DUPR is a live snapshot; some accounts are stale (see the last-match dates in the data).

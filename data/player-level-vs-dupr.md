# Apex Player Level vs. DUPR Rating

_Generated 2026-07-20 from `events.json` (Apex Pickleball Clubs, Cedar Park TX) cross-referenced against DUPR (dupr.com) player search._

## Method

- **Apex level**: Apex/PodPlay runs sessions in fixed bands — Level 1B (0.5), 1+ (1.0), 2 (2.0), 2+ (2.9), 3 (3.0), 3+ (3.9), 4 (4.0), 4+ (4.9), 5 (5.0), 6 (6.0) — confirmed from the `minRating`/`maxRating` on each event in `events.json`. A player's Apex rating here is the average of the per-session rating recorded for them at every session they attended; almost everyone's lands exactly on one band value, but a few sit between two bands (shown as e.g. "between L1+ and L2") either because they were recorded slightly inside a band or because they attended sessions from more than one band.
- **DUPR rating**: looked up live via DUPR's player-search API, biased to the Cedar Park, TX area. When a name matched multiple DUPR accounts, the one located in the Austin metro area was used; if several Austin-area accounts shared the same name, the one whose DUPR rating was numerically closest to the player's Apex rating was picked as the tie-break (noted in the table).
- **DUPR reliability score**: DUPR's own 0-100 confidence score for that rating (more matches played → higher reliability; a rating based on very few games can carry a real number but low reliability). Shown for both doubles and singles alongside each rating.
- **Last DUPR game**: the date of the player's most recent recorded DUPR match (either format, whichever is more recent), pulled from their DUPR match history. Blank means DUPR has no rated match on file for them yet.
- **Confidence** (mine, not DUPR's): `high` = one unambiguous Austin-metro account. `medium` = disambiguated via the rating tie-break, or found only after trying a nickname/title/hyphenated-name variant. `low` = a real match but with meaningful uncertainty (e.g. only a first name + last initial to go on, or an unclaimed profile with no location to confirm).
- Players with no DUPR account findable near Austin (private, unrated, or truly not on DUPR) are listed as **not found** rather than guessed.
- **Hand-reviewed pass**: every `low`-confidence match and every "not found" case was manually re-checked against the raw candidate list, not just the automated tie-break. This fixed mislabeled matches (a short-but-real surname like "Yu", or a `Jr` suffix, had been wrongly flagged as an uncertain fragment), recovered a handful of unclaimed/no-location DUPR profiles that are the only account worldwide with that exact name, filled in the account owner's own profile (DUPR excludes your own logged-in account from its own search results), and walked back two guesses (`SR T`, `J O`) to *not found* because the closest automatic "match" didn't actually resemble the name once inspected directly.
- **Deeper retry pass**: every remaining "not found" player was retried with name-order swaps, nickname expansions, hyphenated-name splits, and a wider search radius. Out of 88 retried, this only turned up 4 trustworthy new matches (both the first *and* last name lined up, via an exact match or a real nickname/hyphen split) — the rest of the retry's "hits" matched on only a first *or* last name and turned out to be a completely different real person on inspection, so they were rejected rather than reported as a match.

## Summary

- **308** players had an Apex rating on file.

- **191** were matched to a DUPR account with a numeric doubles rating — this is the chartable set.

- **32** matched a DUPR account, but that account has no doubles rating yet (`NR`).

- **85** had no findable DUPR account near Austin, even after the deeper retry pass.

- Average (Apex − DUPR) = **-0.06**. 57 players are rated **≥0.3 higher** on Apex than on DUPR, 64 are rated **≥0.3 lower**, and 70 are within ±0.3 (roughly in line).

## Level vs. DUPR chart

![Apex rating vs DUPR rating scatter plot](dupr/level_vs_dupr.png)

Points above the dashed line play a *better* real DUPR than their Apex level suggests; points below play *worse* — i.e. their Apex level overstates them.

![Distribution of Apex minus DUPR](dupr/level_vs_dupr_delta.png)

## Full player table

Sorted by number of Apex sessions attended (most active first). Reliability is DUPR's own 0-100 confidence score for that rating. A [CSV export](player-level-vs-dupr.csv) with the same data (plus not-found rows) is also available.

| Player | Sessions | Apex level | DUPR name | DUPR ID | Location | DUPR doubles | Doubles reliability | DUPR singles | Singles reliability | Last DUPR game | Confidence | Notes |
|---|---:|---|---|---|---|---:|---:|---:|---:|---|---|---|
| David Pierce | 18 | 2 | David Pierce | VXW207 | Cedar Park, TX, US | 3.038 | 100 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Agent Art Ofiaza | 16 | 2+ | Arthur Ofiaza | YM46KP | Austin, TX, US | 3.337 | 10 | 3.293 | 30 | 2026-04-25 | medium | single Austin-metro match (via variant 'Art Ofiaza') |
| Ronnie S | 15 | 2+ | ronnie sng | 4VNRQK | Austin, TX, US | 2.033 | 10 | — | 0 | 2025-07-12 | low | single Austin-metro match; original name had a bare initial, treat match as uncertain |
| Evan Tran | 14 | 4 | Evan Transue | 17PMP5 | Austin, TX, US | 4.202 | 30 | 3.542 | 10 | 2025-06-07 | medium | tie-break among 2 Austin-metro candidates by rating |
| Avinash Bhandari | 14 | 4 | Avinash Bhandari | ZDL6NW | — | 3.701 | 10 | — | 0 | 2026-06-04 | medium | tie-break among 2 Austin-metro candidates by rating |
| Captain Kyle Dunn | 14 | 3 | Kyle Dunn | 6PW6DD | Leander, TX, US | 2.923 | 50 | — | 0 | 2026-06-28 | medium | single Austin-metro match (via variant 'Kyle Dunn') |
| Julie Jasiota | 13 | 2 | Julie Jasiota | D9NLKM | Pflugerville, TX, US | 2.232 | 10 | — | 0 | 2025-03-24 | high | single Austin-metro match |
| Keith Higbee | 13 | 2 | Keith Higbee | W672LY | — | 2.865 | 1 | — | 0 | 2023-10-18 | low | only DUPR account worldwide with this exact name; location unconfirmed |
| Clark Bruce | 13 | 3 | Clark Bruce | V2GJ9J | Cedar Park, TX, US | — | — | — | — | — | low | ambiguous among 2 Austin-metro candidates (no ratings to tie-break), picked nearest |
| Venkat Raavi | 13 | 5 | Venkata Raavi | 76OJX4 | Leander, TX, US | 4.225 | 100 | — | 0 | 2026-02-18 | high | single Austin-metro match |
| David Cardona | 13 | 3+ | David Cardona | MPLQ5G | Leander, TX, US | 3.282 | 40 | — | 0 | 2026-06-28 | high | single Austin-metro match |
| Art Irwin | 12 | 2+ | Art Irwin | KZ42ZY | Cedar Park, TX, US | 2.634 | 50 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Jennifer Dunn | 12 | 2 | Jennifer Dunn | 4Q9E5M | Cedar Park, TX, US | 2.803 | 20 | — | 0 | 2026-04-26 | high | single Austin-metro match |
| Udit D | 12 | 3+ | Udit Dadwani | 9959YR | Austin, TX, US | 2.919 | 60 | — | 0 | 2025-12-20 | low | tie-break among 2 Austin-metro candidates by rating; original name had a bare initial, treat match as uncertain |
| Josh Gleich | 11 | 4 | Josh Gleich | 3VW56J | Austin, TX, US | 3.774 | 100 | 3.789 | 10 | 2026-07-14 | high | single Austin-metro match |
| Christine  OLeary | 11 | 3 | Christine OLeary | L5YZN5 | Austin, TX, US | 3.273 | 30 | — | 0 | 2025-07-09 | medium | single Austin-metro match (via variant 'Christine OLeary') |
| Dan Tran | 11 | 3 | Dan Tran | V2L9D7 | Austin, TX, US | 3.203 | 70 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Ling-Yu Kan | 10 | 2 | Ling-Yu Kan | GWLWPQ | Cedar Park, TX, US | 2.484 | 70 | — | 0 | 2026-05-22 | high | single Austin-metro match |
| Sue Whieldon | 10 | 3+ | Sue Whieldon | YGWP6D | Leander, TX, US | 3.759 | 60 | — | 0 | 2026-04-26 | high | single Austin-metro match |
| Christine McCully | 10 | 3 | Christine  McCully | WZRN5G | Cedar Park, TX, US | 2.361 | 10 | — | 0 | 2026-05-16 | high | single Austin-metro match |
| Dennis Porter | 10 | 4 | Dennis Porter | ZNVZ4P | Cedar Park, TX, US | 3.242 | 100 | 3.25 | 60 | 2026-07-18 | high | single Austin-metro match |
| Chris Wiles Wiles | 10 | 3+ | Christopher Wiles | NRYG52 | Cedar Park, TX, US | 3.351 | 100 | 3.799 | 1 | 2026-07-11 | high | DUPR excludes your own logged-in account from search results; filled in directly from your profile page. |
| Ravi Sherom | 10 | 3+ | Ravi Sheromani | XON7D4 | Leander, TX, US | 3.282 | 40 | — | 0 | 2026-06-28 | high | single Austin-metro match |
| Marion Serelis | 10 | 2 | Marion Serelis | VXXNV7 | Austin, TX, US | 2.331 | 90 | — | 0 | 2026-04-29 | high | single Austin-metro match |
| Penny Goh | 10 | 2 | Penny Goh | J5NQ74 | Williamson County, TX, US | 2.23 | 1 | — | 0 | 2025-09-06 | high | single Austin-metro match |
| Ryan Church | 10 | 2 | Ryan Church | 6N9XV0 | Leander, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Bojidar (Buddy) Kraptchev | 9 | 2+ | Bojidar Kraptchev | X0DZ95 | Austin, TX, US | 2.863 | 30 | — | 0 | 2026-06-28 | medium | single Austin-metro match (via variant 'Bojidar Kraptchev') |
| Y Lu | 9 | 2 | Yvonne Lu | RZP9WZ | Austin, TX, US | 2.787 | 1 | — | 0 | 2024-07-28 | medium | tie-break among 4 Austin-metro candidates by rating |
| Alexandra Klose | 9 | 2 | Alexandra Klose | 7ZP0D9 | Leander, TX, US | 2.792 | 60 | — | 0 | 2026-07-18 | high | single Austin-metro match |
| Melissa Yeilding | 9 | 3+ | Melissa Yeilding | 94DZVR | Cedar Park, TX, US | 3.416 | 30 | — | 0 | 2025-08-24 | high | single Austin-metro match |
| David Richter | 9 | 3 | David Richter | 0RZ2JQ | — | — | — | — | — | — | low | only DUPR account worldwide with this exact name; location unconfirmed |
| AJ Mitchell | 9 | 2+ | AJ Mitchell | 6KY26G | Leander, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Julia Hall | 9 | 1+ | Julia Scariot Haller | EWQWYM | Austin, TX, US | 3.005 | 100 | — | 0 | 2026-07-14 | high | single Austin-metro match |
| Lauren Konogeris | 9 | 3 | Lauren Konogeris | 990Q2E | Georgetown, TX, US | 3.294 | 100 | — | 0 | 2026-07-13 | high | single Austin-metro match |
| Pam Williamson | 9 | 2 | Pam  Williamson | L2ZQR6 | Cedar Park, TX, US | 2.592 | 100 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Sonny Vongtip | 8 | 3+ | Sonny  Vongtip | K5OMW7 | Cedar Park, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Lionel LeBlanc | 8 | 2 | Lionel LeBlanc | DNQDGL | Leander, TX, US | 2.735 | 40 | — | 0 | 2025-08-03 | high | single Austin-metro match |
| Cheryl Mulloy | 8 | 3 | Cheryl Mulloy | ZNV06W | Leander, TX, US | 3.078 | 100 | — | 0 | 2026-06-14 | high | single Austin-metro match |
| Byron Williams | 8 | 3 | Byron Williams | EG9VXW | Austin, TX, US | 3.221 | 30 | — | 0 | 2024-08-15 | high | single Austin-metro match |
| K Madras | 8 | 2+ | Karthik Madras | V6RXEE | Austin, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Harold Arias | 8 | 4 | Harold Arias | MP5VYO | Cedar Park, TX, US | 3.686 | 20 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Peyton Tran | 8 | 4 | Peyton Tran | NX0GEZ | Austin, TX, US | 3.116 | 20 | — | 0 | 2026-06-28 | high | single Austin-metro match |
| Glen Reilly | 8 | 2+ | Glen Reilly | YX4GPG | Georgetown, TX, US | 3.224 | 60 | 3.294 | 10 | 2025-08-28 | high | single Austin-metro match |
| Van Putman | 7 | 4 | Van Putman | YNK0PD | Round Rock, TX, US | 3.058 | 10 | — | 0 | 2026-05-03 | high | single Austin-metro match |
| Tracy Bombarger | 7 | 2 | Tracy Bombarger | WK254K | Cedar Park, TX, US | 2.677 | 100 | — | 0 | 2026-06-22 | high | single Austin-metro match |
| Carmen Sotillo | 7 | 2 | Carmen Sotillo | 2PJMZ4 | Round Rock, TX, US | 2.592 | 90 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Biswajit Swain | 7 | 3+ | Biswajit Swain | 94MYYK | Cedar Park, TX, US | 3.266 | 1 | — | 0 | 2025-03-11 | high | single Austin-metro match |
| Brian Henry | 7 | 2 | Brian Henry | JZROEW | Austin, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Paul Escobedo | 7 | 2+ | Paul Escobedo | J5PGVJ | Georgetown, TX, US | 2.522 | 10 | — | 0 | 2026-04-26 | high | single Austin-metro match |
| Ruben Reyes | 7 | 4 | Ruben Reyes | 3L5JZ1 | Cedar Park, TX, US | 3.642 | 100 | — | 0 | 2026-05-09 | high | single Austin-metro match |
| Jen Wang | 7 | 3 | Jennifer Wang | VX60GE | Cedar Park, TX, US | 3.201 | 100 | 3.201 | 1 | 2026-07-14 | high | single Austin-metro match |
| Windy Smith | 7 | 3 | Windy Smith | O69EOL | Round Rock, TX, US | 2.91 | 100 | 2.161 | 60 | 2026-07-14 | medium | tie-break among 2 Austin-metro candidates by rating |
| Ashok Perera | 7 | 2 | Ashok Perera | PZ65QZ | Austin, TX, US | 3.925 | 1 | — | 0 | 2025-06-12 | high | single Austin-metro match |
| James Eargle | 7 | 3+ | James Eargle | X2WJ64 | Round Rock, TX, US | 3.249 | 30 | — | 0 | 2025-10-19 | high | single Austin-metro match |
| Matt Yeilding | 7 | 3+ | Matt Yeilding | Q5MMR5 | Austin, TX, US | 3.402 | 10 | — | 0 | 2025-08-26 | high | single Austin-metro match |
| Kelly Walenta | 6 | 2 | Kelly  Walenta | 557M5P | Leander, TX, US | 2.443 | 100 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Denni Northway | 6 | 3 | Denni Northway | YGLD6K | Round Rock, TX, US | 2.989 | 90 | — | 0 | 2026-05-07 | high | single Austin-metro match |
| Brian Hundsdorfer | 6 | 3 | Brian Hundsdorfer | E9ENDJ | Cedar Park, TX, US | 3.255 | 100 | — | 0 | 2026-06-13 | high | single Austin-metro match |
| David Knoll | 6 | 3 | David Knoll | 6NZQGG | Leander, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Wayne Smith | 6 | 3 | Wayne Smith | 9PGDNR | Austin, TX, US | 3.386 | 1 | — | 0 | 2024-01-14 | high | single Austin-metro match |
| Huong Dang | 6 | 3 | Huong Dang | E9RZMV | Austin, TX, US | 3.707 | 20 | — | 0 | 2026-04-25 | high | single Austin-metro match |
| Stacie Pacitti | 6 | 2+ | Stacie Pacitti | YNYM6K | Austin, TX, US | 3.636 | 70 | — | 0 | 2026-05-11 | high | single Austin-metro match |
| Lianne VanDyke | 6 | 3+ | Lianne VanDyke | RYD7ON | Cedar Park, TX, US | 3.363 | 100 | 2.328 | 10 | 2026-07-05 | high | single Austin-metro match |
| Sumanth Inaganti | 6 | 3 | Sumanth Inaganti | G0GQPV | Austin, TX, US | 3.559 | 100 | — | 0 | 2026-07-18 | high | single Austin-metro match |
| Michael Yeh | 6 | 5 | Michael Yeh | 3OWXP8 | Austin, TX, US | 4.379 | 50 | 4.741 | 30 | 2026-04-23 | high | single Austin-metro match |
| Jill Bunn | 5 | 1.9 (between L1+ and L2) | Jill Bunn | EXYL0M | Leander, TX, US | 2.746 | 60 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Oscar Aviles | 5 | 4 | Oscar Aviles | XKJYJ2 | Austin, TX, US | 3.749 | 100 | 2.925 | 10 | 2026-07-11 | high | single Austin-metro match |
| Jasvinder (Jesse) Deol | 5 | 4 | Jasvinder Deol | 6NNDLQ | Georgetown, TX, US | 3.71 | 20 | — | 0 | 2026-04-25 | medium | single Austin-metro match (via variant 'Jasvinder Deol') |
| Stacy White | 5 | 1+ | Stacy White | 4Q974K | Leander, TX, US | 2.307 | 70 | — | 0 | 2026-05-22 | high | single Austin-metro match |
| Jonathon Kennemer | 5 | 2+ | Jonathon Kennemer | KZZ2LQ | Leander, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Cori Cline | 5 | 3+ | Cori Cline | GGVK0D | Austin, TX, US | 3.174 | 100 | 2.442 | 20 | 2026-07-12 | high | single Austin-metro match |
| Dan Chaplin | 5 | 3 | Dan Chaplin | GGROMV | Austin, TX, US | 3.16 | 40 | 2.894 | 10 | 2025-08-12 | high | single Austin-metro match |
| Henry "Hank" Amen | 5 | 3 | Henry Hank Amen | 0YJ674 | Cedar Park, TX, US | 2.896 | 30 | — | 0 | 2026-02-20 | high | single Austin-metro match |
| Michael Sigman | 5 | 3 | Michael Sigman | 17DV48 | Leander, TX, US | 3.088 | 100 | 3.321 | 30 | 2026-06-14 | high | single Austin-metro match |
| Rick Allard | 5 | 3+ | Rick Allard | 76N704 | Leander, TX, US | 3.74 | 100 | 3.683 | 10 | 2026-07-11 | high | single Austin-metro match |
| Lisa Macs | 5 | 1+ | Lisa Macs | 5Y2XOR | Cedar Park, TX, US | 2.222 | 90 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Raj Akshatha | 5 | 2+ | Akshatha Raj | V2ZL65 | Austin, TX, US | 2.717 | 1 | — | 0 | 2025-11-16 | high | single Austin-metro match |
| Aravind Sethurathnam | 5 | 4 | ARAVIND  Sethurathnam | 2Z0LO9 | Leander, TX, US | 3.614 | 100 | — | 0 | 2026-05-23 | high | single Austin-metro match |
| Seth Moore | 5 | 2 | Seth Moore | 7ZZKGM | Leander, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Claudia Salty | 5 | 2+ | claudia salty | RYDQ7Z | Austin, TX, US | 2.653 | 100 | — | 0 | 2026-06-14 | high | single Austin-metro match |
| Thao Tran | 5 | 3 | Thao Tran | Y4DPZK | Cedar Park, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Rebecca Hwang | 5 | 3 | Rebecca Hwang | D94EOY | Cedar Park, TX, US | 2.706 | 70 | — | 0 | 2026-06-28 | high | single Austin-metro match |
| Anthony Williams | 5 | 4 | Anthony Williams | DNQXXX | Austin, TX, US | 3.37 | 30 | — | 0 | 2026-05-01 | high | single Austin-metro match |
| Grace Wayman | 5 | 3 | Grace Wayman | 7DKLEN | Austin, TX, US | 2.493 | 50 | — | 0 | 2026-06-28 | high | single Austin-metro match |
| Rhea Fryar | 5 | 2+ | Rhea Fryar | KXM6NO | Cedar Park, TX, US | 2.661 | 100 | — | 0 | 2026-07-14 | high | single Austin-metro match |
| David Anderson | 4 | 4 | David Anderson | YG2PZG | Leander, TX, US | 3.874 | 70 | — | 0 | 2026-05-16 | high | single Austin-metro match |
| Paul Joung | 4 | 4 | Paul Joung | MEPM6D | Austin, TX, US | 3.753 | 100 | — | 0 | 2026-05-02 | high | single Austin-metro match |
| Evan Shuvo | 4 | 4+ | Evan Shuvo | 1Q5DN3 | Leander, TX, US | 4.006 | 100 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Amy Mullins | 4 | 2 | Amy mullins | L54EZK | Williamson County, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Malee Hundsdorfer | 4 | 2 | Malee Hundsdorfer | GW0WYM | Cedar Park, TX, US | 2.426 | 100 | — | 0 | 2026-06-08 | high | single Austin-metro match |
| Missy Lipscomb | 4 | 2 | Missy Lipscomb | 59RKKL | Cedar Park, TX, US | 2.727 | 100 | — | 0 | 2026-05-14 | high | single Austin-metro match |
| Sarah Moore | 4 | 2 | Sarah Moore | N509JZ | Leander, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Monica Ng | 4 | 1+ | Monica Ng | WZ2V4G | Austin, TX, US | — | — | — | — | — | low | ambiguous among 2 Austin-metro candidates (no ratings to tie-break), picked nearest |
| Roxanne Redwine | 4 | 3+ | Roxanne Redwine | 3P55MZ | Leander, TX, US | 3.345 | 40 | — | 0 | 2025-09-29 | high | single Austin-metro match |
| Vishal Raghuvanshi | 4 | 3 | Vishal Raghuvanshi | 0PR9N4 | Leander, TX, US | 3.303 | 20 | — | 0 | 2026-06-27 | high | single Austin-metro match |
| Amanda Reese | 4 | 3 | Amanda Reese | 592KDP | Cedar Park, TX, US | 3.093 | 100 | 2.772 | 10 | 2026-07-13 | high | single Austin-metro match |
| Sol Cowes | 4 | 3 | SolBrett Cowes | PK7D2M | — | 3.394 | 100 | — | 0 | 2026-06-28 | high | single Austin-metro match |
| Jen Riley | 4 | 3+ | Jennifer Riley | X2EV47 | Austin, TX, US | 3.331 | 60 | 3.452 | 1 | 2025-10-19 | high | single Austin-metro match |
| Dani Hunter | 4 | 4 | Dani Hunter | NYQOP7 | Austin, TX, US | 3.814 | 100 | — | 0 | 2026-04-25 | high | single Austin-metro match |
| Ryan Garoogian | 4 | 3+ | Ryan Garoogian | MP0D5D | Austin, TX, US | 3.771 | 50 | — | 0 | 2026-03-25 | high | single Austin-metro match |
| Jin H Liu | 4 | 3+ | Jinhong Liu | 6P6WZ0 | Austin, TX, US | 2.229 | 70 | — | 0 | 2026-04-19 | medium | recovered on deeper hand-reviewed retry: middle initial matches the DUPR account's compound given name (Jinhong), exact surname match |
| Austin Tong | 4 | 3 | Austin Tong | RWK6DN | Austin, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Mike Nguyen | 4 | 3 | Mike Nguyen | 9DYXQE | Cedar Park, TX, US | 2.946 | 50 | — | 0 | 2026-05-23 | high | single Austin-metro match |
| bill oleary | 4 | 2 | bill oleary | XKOEDR | — | — | — | — | — | — | low | only DUPR account worldwide with this exact name; location unconfirmed |
| Ted Dimbero | 4 | 2 | Ted (Edward)  Dimbero | DY9PM6 | Williamson County, TX, US | 2.568 | 70 | — | 0 | 2026-02-08 | high | single Austin-metro match |
| Tiffany Chambers | 3 | 3 | Tiffany Chambers | 6NW7GD | Lake Saint Louis, MO, US | 3.405 | 100 | — | 0 | 2026-04-19 | low | only DUPR account worldwide with this exact name; location unconfirmed |
| Leah Gibson | 3 | 4+ | Leah Gibson | L2KXV5 | Austin, TX, US | 3.951 | 80 | — | 0 | 2026-04-27 | high | single Austin-metro match |
| Tim Redwine | 3 | 4 | Tim Redwine | 8MP6QP | Leander, TX, US | 4.114 | 30 | — | 0 | 2025-01-16 | medium | tie-break among 2 Austin-metro candidates by rating |
| Debera Stein | 3 | 2 | Debera Stein | M2079P | — | 2.629 | 1 | — | 0 | 2024-04-04 | low | only DUPR account worldwide with this exact name; location unconfirmed |
| Sean Sasser | 3 | 3+ | Sean Sasser | 4VQQRG | Cedar Park, TX, US | 3.396 | 80 | — | 0 | 2026-01-31 | high | single Austin-metro match |
| Bryan Gabbert | 3 | 5 | Bryan Gabbert | 16MYRG | Cedar Park, TX, US | 4.29 | 100 | 3.984 | 10 | 2026-07-12 | high | single Austin-metro match |
| Shelly Molina | 3 | 1+ | Shelly Molina | WNOWYQ | Point Venture, TX, US | 2.078 | 90 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Alice Lequin | 3 | 2+ | Alice Lequin | VLXYQ6 | Leander, TX, US | 2.792 | 20 | — | 0 | 2026-06-28 | high | single Austin-metro match |
| Archie Imperial | 3 | 4 | Archie Imperial | ZNK6MW | Cedar Park, TX, US | 3.066 | 60 | — | 0 | 2026-05-02 | high | single Austin-metro match |
| Lori Gibbens | 3 | 4 | Lori Gibbens-Bell | 8E9QQW | Leander, TX, US | 4.222 | 30 | — | 0 | 2025-06-09 | high | single Austin-metro match |
| Austin Steadman | 3 | 4+ | Austin Steadman | GG5REG | Leander, TX, US | 3.769 | 100 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Bryson Renouard | 3 | 5 | Bryson Renouard | O6ELLP | Austin, TX, US | 3.835 | 70 | 3.6 | 40 | 2026-02-01 | high | single Austin-metro match |
| TUNG GIANG | 3 | 5 | Tung Giang | XJNEZR | Cedar Park, TX, US | 4.133 | 1 | — | 0 | 2025-02-03 | high | single Austin-metro match |
| Patty Jistel | 3 | 2+ | Patty Jistel | 7ZWOQ4 | Austin, TX, US | 3.023 | 90 | — | 0 | 2026-05-22 | high | single Austin-metro match |
| Sherry Winn | 3 | 2 | Sherry Winn | V20NZJ | Leander, TX, US | 2.058 | 100 | — | 0 | 2026-05-04 | high | single Austin-metro match |
| Nicole Bell | 3 | 3+ | Nicole Bell | ZDZGVL | Georgetown, TX, US | 3.4 | 100 | — | 0 | 2026-04-25 | high | single Austin-metro match |
| Carla Carrasco | 3 | 2 | Carla Carrasco | Q5NWL0 | Austin, TX, US | 2.645 | 70 | — | 0 | 2026-04-11 | high | single Austin-metro match |
| Erin Price | 3 | 1+ | Erin Price | 8K2VO6 | Cedar Park, TX, US | 2.282 | 30 | — | 0 | 2025-08-31 | high | single Austin-metro match |
| Jorge Taboada | 3 | 3+ | Jorge Taboada | 8MQR6G | Austin, TX, US | 3.659 | 80 | 3.706 | 30 | 2026-07-11 | high | single Austin-metro match |
| Tim Moore | 3 | 4 | Tim Moore | Z9676D | Round Rock, TX, US | 3.488 | 30 | — | 0 | 2025-04-22 | high | single Austin-metro match |
| Vonda Ilseng | 3 | 2 | Vonda Ilseng | VX6REP | Cedar Park, TX, US | 2.762 | 90 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Jan Filsinger | 2 | 2+ | Jan Filsinger | YNMX4E | Cedar Park, TX, US | 2.404 | 10 | — | 0 | 2026-02-08 | high | single Austin-metro match |
| Philip Johnson | 2 | 2 | Philip Johnson | RDYR7D | Leander, TX, US | 2.404 | 10 | — | 0 | 2026-02-08 | high | single Austin-metro match |
| Nishanth Nair | 2 | 2+ | Nishanth Nair | RYYJMM | Austin, TX, US | 3.269 | 60 | — | 0 | 2026-05-10 | high | single Austin-metro match |
| Amit Sehgal | 2 | 4 | Amit Sehgal | YGN7NG | Leander, TX, US | 3.437 | 100 | — | 0 | 2026-05-18 | high | single Austin-metro match |
| Hari Tulabandula | 2 | 5 | Hari Tulabandula | XOJ0E7 | Leander, TX, US | 3.955 | 70 | — | 0 | 2026-02-18 | high | single Austin-metro match |
| Andrea Morris | 2 | 1+ | Andrea  Morris | D5M4Y4 | Cedar Park, TX, US | 2.012 | 50 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Nancy boxwell | 2 | 1+ | Nancy Boxwell | ONRKLL | Lago Vista, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Gracie Larrea | 2 | 2 | Gracie Larrea | QPJWW0 | Cedar Park, TX, US | 2.139 | 80 | — | 0 | 2026-05-22 | high | single Austin-metro match |
| Walter Sotillo | 2 | 3+ | Walter Sotillo | EXDP6J | Round Rock, TX, US | 2.845 | 10 | — | 0 | 2026-06-05 | high | single Austin-metro match |
| Terry Harper | 2 | 5 | Terry Harper | 3PZYZ1 | Cedar Park, TX, US | 5.218 | 30 | — | 0 | 2023-07-26 | high | single Austin-metro match |
| Tatchi Lay | 2 | 5 | Tatchi Lay | 3XDVX1 | Austin, TX, US | 4.187 | 70 | — | 0 | 2026-04-23 | high | single Austin-metro match |
| Frank Lofton | 2 | 2 | Frank Lofton | V2V90P | Cedar Park, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Sonia Lofton | 2 | 1+ | Sonia Lofton | 5YGEGP | Cedar Park, TX, US | 2.801 | 90 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Becky Duenas | 2 | 2 | Rebecca Duenas | Z4J2NQ | Cedar Park, TX, US | 2.546 | 70 | — | 0 | 2026-07-14 | medium | recovered on deeper hand-reviewed retry: nickname (Becky/Rebecca) + exact surname match |
| Steve Bronson | 2 | 3 | Steve Bronson | 30KZDG | Georgetown, TX, US | 3.167 | 80 | — | 0 | 2026-03-08 | high | single Austin-metro match |
| Rhonda Jenkins | 2 | 2+ | RHONDA JENKINS | 3LZR5Z | Austin, TX, US | 2.656 | 50 | — | 0 | 2026-02-19 | high | single Austin-metro match |
| Robert Weber | 2 | 4 | Robert Weber | 3Y6MVE | Cedar Park, TX, US | 3.793 | 100 | — | 0 | 2026-05-23 | high | single Austin-metro match |
| Aryan M | 2 | 5 | Aryan Malhotra | 0QWPNQ | Leander, TX, US | 3.906 | 100 | 4.19 | 100 | 2026-07-18 | low | tie-break among 2 Austin-metro candidates by rating; original name had a bare initial, treat match as uncertain |
| Joyce Gibson | 2 | 2+ | Joyce Gibson | 5EEMKR | Leander, TX, US | 2.796 | 100 | — | 0 | 2026-06-14 | high | single Austin-metro match |
| Devin Burch | 2 | 3 | Devin Burch | 2Y7P2Y | Cedar Park, TX, US | 2.99 | 70 | — | 0 | 2026-06-28 | high | single Austin-metro match |
| mason currie | 2 | 3 | mason currie | G0O2XM | Austin, TX, US | 3.382 | 40 | — | 0 | 2026-07-11 | high | single Austin-metro match |
| Joshi Mendieta | 2 | 2+ | Joshi Mendieta | G0MEEV | Leander, TX, US | — | — | — | — | — | high | single Austin-metro match |
| James Johnson | 2 | 3 | James Johnson | OZN2KW | Belton, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Bill Findley | 2 | 3 | William Findley | 7DMEVM | Lago Vista, TX, US | 3.171 | 1 | — | 0 | 2025-07-14 | medium | single Austin-metro match (via variant 'William Findley') |
| Bailey Kafer | 2 | 3 | Bailey  Kafer | 7JZWM0 | Cedar Park, TX, US | 2.906 | 10 | — | 0 | 2025-11-17 | high | single Austin-metro match |
| Rachel Callihan | 2 | 2 | Rachel Callihan | N5O7Z2 | Cedar Park, TX, US | 2.502 | 90 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Kit Harper | 2 | 4+ | Kit Harper | R8J5M8 | Cedar Park, TX, US | 5.148 | 10 | — | 0 | 2022-03-26 | high | single Austin-metro match |
| Erin Hernandez | 2 | 3+ | Erin Hernandez | 8JMQ9O | Leander, TX, US | 3.699 | 100 | — | 0 | 2026-05-09 | high | single Austin-metro match |
| Robin Reich | 2 | 3 | Robin Reich | 4LK4M6 | Round Rock, TX, US | 3.152 | 70 | — | 0 | 2026-05-16 | high | single Austin-metro match |
| Dianne Hall | 2 | 2 | Dianne Hall | G0XJ5G | Cedar Park, TX, US | 2.244 | 100 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Jules Culin | 2 | 4 | Jules Culin | 84RQVG | Georgetown, TX, US | 4.305 | 80 | 4.03 | 30 | 2026-07-11 | high | single Austin-metro match |
| Dana Turner | 1 | 2 | Dana Turner | MEVRZV | Austin, TX, US | 2.381 | 20 | — | 0 | 2026-02-08 | high | single Austin-metro match |
| Logan  Turner | 1 | 2 | Logan Turner | 4EVRKG | Austin, TX, US | — | — | — | — | — | medium | single Austin-metro match (via variant 'Logan Turner') |
| Mark Mumaw | 1 | 2 | Mark Mumaw | 6765MK | Austin, TX, US | 2.635 | 100 | 2.613 | 10 | 2026-05-04 | high | single Austin-metro match |
| Nazir Siddiqi | 1 | 3+ | Nazir  Siddiqi | RXRJPD | Cedar Park, TX, US | 2.97 | 60 | — | 0 | 2025-10-24 | high | single Austin-metro match |
| John Cogdell | 1 | 3+ | John Cogdell | 76ZZ24 | Austin, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Ling Wang | 1 | 4 | Ling Wang | KXP60Q | Austin, TX, US | 3.636 | 1 | 3.317 | 10 | 2025-02-16 | high | single Austin-metro match |
| Kristy Cravey | 1 | 2 | Kristy Cravey | Z9RXMM | — | 2.629 | 1 | — | 0 | 2024-04-04 | low | only DUPR account worldwide with this exact name; location unconfirmed |
| Adrian  Godoy | 1 | 2 | Adrian Godoy | 4Q60KK | Leander, TX, US | 2.738 | 70 | 2.194 | 30 | 2026-07-18 | medium | single Austin-metro match (via variant 'Adrian Godoy') |
| Sandy  Ross | 1 | 2 | Sandy Ross | VXZ0G5 | Cedar Park, TX, US | 2.943 | 90 | — | 0 | 2026-05-11 | medium | single Austin-metro match (via variant 'Sandy Ross') |
| Jeremy Craig | 1 | 5 | Jeremy Craig | DNEN5X | Jackson, TN, US | 3.703 | 100 | 3.415 | 10 | 2026-06-15 | low | only DUPR account worldwide with this exact name; location unconfirmed |
| Jeff Nowotny | 1 | 5 | Jeff Nowotny | YNJEJE | Austin, TX, US | 4.587 | 1 | — | 0 | 2025-01-31 | high | single Austin-metro match |
| Rolando Fuertes Jr | 1 | 1+ | Rolando Fuertes Jr | XKZ567 | Cedar Park, TX, US | 2.687 | 100 | — | 0 | 2026-01-20 | high | single Austin-metro match |
| Henry Marshall | 1 | 3+ | henry marshall | 7DR2P4 | Cedar Park, TX, US | 3.632 | 30 | — | 0 | 2025-08-23 | high | single Austin-metro match |
| Daniel Quach | 1 | 3+ | Daniel Quach | EWV5NW | Cedar Park, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Becky McGillick | 1 | 3+ | Becky McGillick | 177PL5 | Austin, TX, US | 3.68 | 100 | 2.767 | 70 | 2026-07-12 | high | single Austin-metro match |
| Karen Wilkins | 1 | 2+ | Karen Wilkins | D9YQP6 | Leander, TX, US | 2.881 | 100 | — | 0 | 2026-06-28 | high | single Austin-metro match |
| Bill Wilkins | 1 | 2+ | Bill Wilkins | 4VPKN2 | Leander, TX, US | 2.209 | 50 | — | 0 | 2026-06-14 | high | single Austin-metro match |
| Emily Craig | 1 | 2+ | Emily Craig | Z9K5GD | Austin, TX, US | 2.679 | 40 | — | 0 | 2026-02-08 | high | single Austin-metro match |
| Matt Fosbury | 1 | 2 | Matthew Fosbury | 2ZVV9E | Round Rock, TX, US | 2.042 | 30 | — | 0 | 2025-08-17 | high | single Austin-metro match |
| Zavian Maredia | 1 | 4 | Zavian Maredia | PPQ5RQ | Bayswater, VIC, AU | 4.106 | 20 | — | 0 | 2026-06-29 | low | only DUPR account worldwide with this exact name; location unconfirmed |
| Lyndie Mitchell | 1 | 1+ | Lyndie Mitchell | X0QQP7 | Leander, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Crystal Murray | 1 | 1B | Crystal Murray | 9004XK | Leander, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Alex Cooke | 1 | 2 | Alex Cooke | Z9XRKQ | Cedar Park, TX, US | 2.699 | 10 | — | 0 | 2024-12-22 | high | single Austin-metro match |
| Paola Aguayo | 1 | 1+ | Paola Aguayo | 94RWO7 | Round Rock, TX, US | 3.462 | 20 | — | 0 | 2025-04-15 | high | single Austin-metro match |
| Vamsi Ponakala | 1 | 3 | Vamsi Ponakala | XK7RX4 | Austin, TX, US | 3.797 | 100 | — | 0 | 2026-07-13 | high | single Austin-metro match |
| Suharno Abdul Rahman | 1 | 3+ | Suharno Abdul Rahman | OZY647 | Williamson County | 3.852 | 100 | 3.532 | 40 | 2026-07-13 | high | single Austin-metro match |
| Kamal Chandrasekaran | 1 | 3+ | Kamal Chandrasekaran | RY4PLM | Leander, TX, US | 3.534 | 30 | — | 0 | 2026-04-25 | high | single Austin-metro match |
| Pradeep Rajurs | 1 | 5 | Pradeep Rajurs | EGV7MJ | Austin, TX, US | 4.31 | 50 | — | 0 | 2026-05-09 | high | single Austin-metro match |
| Diane Eargle | 1 | 3+ | Diane  Eargle | 4Z2VGK | Round Rock, TX, US | 3.229 | 1 | — | 0 | 2025-08-10 | high | single Austin-metro match |
| Nathan Salty | 1 | 3+ | Nathan Salty | 2QV2L9 | Austin, TX, US | 3.206 | 70 | — | 0 | 2026-06-06 | high | single Austin-metro match |
| Breanna Escochea | 1 | 3 | breanna escochea | 6NNG6Q | Cedar Park, TX, US | 3.518 | 20 | — | 0 | 2025-08-23 | high | single Austin-metro match |
| Amanda Arriaga-Braziel | 1 | 1+ | Amanda Braziel | 4PV6WG | Leander, TX, US | 2.358 | 100 | — | 0 | 2026-07-12 | medium | recovered on deeper hand-reviewed retry: exact first name + surname is one half of the hyphenated name on file |
| Elan Lepovic | 1 | 2 | Elan Lepovic | 8GEVVV | Austin, TX, US | 3.134 | 30 | 2.596 | 1 | 2024-09-23 | high | single Austin-metro match |
| Justin Fosbury | 1 | 3+ | Justin Fosbury | 7D5ZK5 | Leander, TX, US | 3.508 | 100 | 3.37 | 20 | 2026-07-12 | high | single Austin-metro match |
| Michelle Yu | 1 | 2 | Michelle Yu | 2ZYG99 | Austin, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Kaylyn Levine | 1 | 4 | Kaylyn Levine | JJMD9O | Georgetown, TX, US | 3.829 | 80 | — | 0 | 2026-04-25 | high | single Austin-metro match |
| Chris Wales | 1 | 3+ | Chris Wales | V7R4LP | Cedar Park, TX, US | 4.002 | 50 | — | 0 | 2025-09-27 | high | single Austin-metro match |
| Teri Citterman | 1 | 3+ | Teri Citterman | JJDEXM | Coco, Provincia de Guanacaste, CR | 3.981 | 1 | — | 0 | 2024-11-10 | low | only DUPR account worldwide with this exact name; location unconfirmed |
| Debra Snyder | 1 | 1+ | Debra  Snyder | PP0GVE | Cedar Park, TX, US | 2.251 | 90 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Kristen Lumsden | 1 | 1+ | Kristen Lumsden | 0P69Y4 | Austin, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Betsy  Escobar | 1 | 2 | betsy escobar | YGL9WD | Cedar Park, TX, US | 2.609 | 60 | — | 0 | 2025-10-20 | medium | single Austin-metro match (via variant 'Betsy Escobar') |
| Akash Bhakta | 1 | 4 | Akash Bhakta | 354YR8 | Austin, TX, US | 4.154 | 30 | 3.895 | 20 | 2024-10-19 | high | single Austin-metro match |
| Patrick Bohrer | 1 | 2+ | Patrick Bohrer | G0WJ7X | — | — | — | — | — | — | low | only DUPR account worldwide with this exact name; location unconfirmed |
| Suzanne brown | 1 | 2 | Suzanne brown | 1NY673 | Austin, TX, US | 3.161 | 10 | — | 0 | 2025-03-27 | high | single Austin-metro match |
| Hong Yang | 1 | 2 | Hong yang | MPPP0L | Austin, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Laura Visser | 1 | 5 | Laura visser | DWRYE4 | Pflugerville, TX, US | 4.17 | 80 | — | 0 | 2026-05-03 | high | single Austin-metro match |
| John Hancock | 1 | 4 | John Hancock | KXEN76 | Cedar Park, TX, US | 3.697 | 40 | — | 0 | 2025-09-25 | medium | tie-break among 2 Austin-metro candidates by rating |
| Samantha Santiago | 1 | 1+ | Samantha De Santiago | JJ9D4D | Williamson County, TX, US | 2.458 | 1 | — | 0 | 2025-04-12 | medium | tie-break among 2 Austin-metro candidates by rating |
| Jenn Partida | 1 | 1+ | Jenn Partida | G7NWQV | Cedar Park, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Rick Johnson | 1 | 2 | Rick Johnson | 3XP221 | Dripping Springs, TX, US | 4.046 | 20 | — | 0 | 2022-11-10 | medium | tie-break among 2 Austin-metro candidates by rating |
| Munir M | 1 | 3+ | Munir Dabaghi | EGW4KW | Leander, TX, US | 3.683 | 70 | — | 0 | 2026-02-14 | low | single Austin-metro match; original name had a bare initial, treat match as uncertain |
| Rob Robinson | 1 | 2 | Kathy Robinson | 4LRVOV | Austin, TX, US | 2.193 | 30 | — | 0 | 2025-05-13 | medium | tie-break among 15 Austin-metro candidates by rating |
| Heather Escobedo | 1 | 1+ | Heather Escobedo | O6Y077 | Leander, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Emily Lai | 1 | 3 | Emily Lai | 7J7NW4 | Austin, TX, US | 3.272 | 20 | — | 0 | 2025-11-16 | high | single Austin-metro match |
| Maria Jackson | 1 | 2 | Maria Jackson | 0QWDZQ | Cedar Park, TX, US | 2.871 | 100 | — | 0 | 2026-06-22 | high | single Austin-metro match |
| Vishal Tasgaonkar | 1 | 5 | Vishal Tasgaonkar | ZNM57D | Williamson County, TX, US | 4.371 | 100 | — | 0 | 2026-05-17 | high | single Austin-metro match |
| Sen Ram | 1 | 3 | Sen Ram | RX92JD | Austin, TX, US | 3.382 | 90 | — | 0 | 2026-05-16 | high | single Austin-metro match |
| Brooke Clancy | 1 | 3 | Brooke Clancy | W64GWY | Leander, TX, US | 2.978 | 100 | — | 0 | 2026-06-14 | high | single Austin-metro match |
| Esmeralda lebaron | 1 | 3 | esmeralda  lebaron | DYXKVY | Leander, TX, US | 2.707 | 100 | — | 0 | 2026-07-14 | high | single Austin-metro match |
| Gregory VonFange | 1 | 5 | Greg VonFange | 175200 | Cedar Park, TX, US | 4.036 | 100 | 3.256 | 20 | 2026-05-23 | medium | recovered on deeper hand-reviewed retry: nickname (Gregory/Greg) + exact surname match, same city |
| Cesar Perez | 1 | 3 | Cesar Perez | Q9LR2N | Austin, TX, US | 3.164 | 10 | — | 0 | 2026-05-04 | medium | tie-break among 2 Austin-metro candidates by rating |
| SHELIA PARODI | 1 | 3+ | Shelia Parodi | 124ZPR | Austin, TX, US | 3.243 | 30 | — | 0 | 2024-06-08 | high | single Austin-metro match |
| Amara Opara | 1 | 2 | Amara Opara | VLXJX5 | Austin, TX, US | 2.703 | 20 | — | 0 | 2026-06-28 | high | single Austin-metro match |
| Lisa Prien | 1 | 2 | Lisa Prien | KDWDQY | Leander, TX, US | 2.452 | 100 | — | 0 | 2026-07-14 | high | single Austin-metro match |
| valeri tate | 1 | 2 | Valeri  Tate | 55456L | Cedar Park, TX, US | — | — | — | — | — | low | ambiguous among 2 Austin-metro candidates (no ratings to tie-break), picked nearest |
| Andrew Solis | 1 | 3 | Andrew Jay Solis | 8K75O7 | Austin, TX, US | 3.411 | 100 | — | 0 | 2026-06-28 | high | single Austin-metro match |
| Zachary Ricketson | 1 | 4 | Zachary  Ricketson | KDKLN7 | Williamson County, TX, US | 3.763 | 100 | — | 0 | 2026-07-11 | high | added manually from a user-supplied DUPR profile link |

## Not found on DUPR

| Player | Sessions | Apex level | Notes |
|---|---:|---|---|
| Edwin Feliciano | 13 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Alet Feliciano | 13 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Steve Felgate | 12 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Robin Felgate | 11 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| John B Mulloy | 11 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Sam Ofiaza | 10 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Daifei Li | 10 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Toni Antov | 9 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Ted Gilkey | 8 | 2+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Adi Gupta | 8 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Juliana Hall | 8 | 1B | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Olivia S Yang | 7 | 4 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| camilleo . | 7 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Mike Wong | 7 | 3 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Amanda Montero | 7 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Ning Shaw | 6 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| SR T | 6 | 4+ | too ambiguous to identify (only initials on file); the closest automatic guess did not actually resemble the name and was dropped on manual review |
| Alfred Zhong | 6 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Matt Hamilton | 6 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Jay Quiocho | 6 | 3 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Harry Rochani | 6 | 3+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Belle Garcia | 6 | 4 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Genie Duvall | 6 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Praveen M | 6 | 3+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Denise  Denicola | 6 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Mohi Muhammed | 5 | 2+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Ale Robles | 5 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Tina Williams | 5 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Sonie Golden | 4 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| John Tao | 4 | 3 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Shun Huang | 4 | 4 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Azusa Manabe | 4 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Steve  Lau | 4 | 3 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Bungbone Naugle | 4 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Michael Gibson | 4 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Miguel Mercado | 4 | 3 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Matt Laakso | 3 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Noah Welker | 3 | 4+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| John McIntyre | 3 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Lacie henry | 3 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Robin Scott | 2 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Olga Panskaya | 2 | 1B | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| SUSAN  Dorsey | 2 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| William  Lindsay | 2 | 3+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Kevin Vorabout | 2 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Janet Snow | 2 | 1B | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Nina Salta | 2 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Parker Speich | 2 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Bhasker M | 2 | 3+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| John Bruker | 2 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Brian Winn | 2 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Andy Steinberg | 2 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Veronica Ochoa | 2 | 2+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Kimberly Steadman | 2 | 4 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Dirk Lammerts | 2 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Kim Phan | 1 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Alexis Gant | 1 | 0.75 (between L1B and L1+) | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| J O | 1 | 1+ | too ambiguous to identify (only initials on file); the closest automatic guess did not actually resemble the name and was dropped on manual review |
| Maxwell Burgess | 1 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Diana Sudduth | 1 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Bruce Cong | 1 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Steven Smith | 1 | 3 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Meredith Putman | 1 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Brian Escochea | 1 | 2+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Rosa Benner | 1 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Christine Scott-Laakso | 1 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| May Dunn | 1 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Jessica Huskisson | 1 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Toby Stevenson | 1 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Raajeev Kalyan | 1 | 3 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Robin Shaw | 1 | 1B | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Jessica Wong | 1 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Luciana Savioli | 1 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Luciana Ladeira | 1 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Jennifer Gardner | 1 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Steve Sherrill | 1 | 1B | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Dawn Sherrill | 1 | 1B | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Greg Berlin | 1 | 0.75 (between L1B and L1+) | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Alanna V | 1 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Melanie Miler | 1 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Kerry McGinty | 1 | 1B | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Sara Henderson | 1 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Kristen Langevin | 1 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Dustin Lange | 1 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Mariana Lange | 1 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |

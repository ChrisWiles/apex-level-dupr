# Apex Player Level vs. DUPR Rating

_Generated 2026-07-20 from the full commit history of `events.json` (Apex Pickleball Clubs, Cedar Park TX -- every player who appears in any of ~70 historical scrapes, not just the current booking window) cross-referenced against DUPR (dupr.com) player search._

## Method

- **Roster scope**: `events.json` only ever shows the current ~2-week booking window, so a single snapshot misses most players. This dataset instead walks every commit that touched `events.json` (~70 snapshots spanning 2026-07-01 to 2026-07-20) and merges every player ever seen, keyed by their stable PodPlay/Firebase account ID -- not by name, since a handful of accounts changed their display name between snapshots (see below).
- **Apex level**: Apex/PodPlay runs sessions in fixed bands -- Level 1B (0.5), 1+ (1.0), 2 (2.0), 2+ (2.9), 3 (3.0), 3+ (3.9), 4 (4.0), 4+ (4.9), 5 (5.0), 6 (6.0). A player's Apex rating here is the average of the per-session rating recorded for them across every session in every snapshot they appeared in (each session counted once, even if it showed up in several consecutive snapshots).
- **DUPR rating**: looked up live via DUPR's player-search API, biased to the Cedar Park, TX area. When a name matched multiple DUPR accounts, the one located in the Austin metro area was used; if several Austin-area accounts shared the same name, the one whose DUPR rating was numerically closest to the player's Apex rating was picked as the tie-break (noted in the table).
- **DUPR reliability score**: DUPR's own 0-100 confidence score for that rating. Shown for both doubles and singles alongside each rating.
- **Last DUPR game**: the date of the player's most recent recorded DUPR match, pulled from their DUPR match history.
- **Confidence** (mine, not DUPR's): `high` = one unambiguous Austin-metro account. `medium` = disambiguated via the rating tie-break, or found only after trying a nickname/title/hyphenated-name variant. `low` = a real match but with meaningful uncertainty (only a first name + last initial to go on, an unclaimed profile with no location to confirm, or a distant match with no closer candidate).
- Players with no DUPR account findable near Austin are listed as **not found** rather than guessed.
- **Name-history matching**: a handful of accounts show up under two different display names across the ~70 snapshots (the same underlying account ID, just edited between scrapes). Where an unmatched player's *other* recorded name turned out to be an exact DUPR match, that's used and clearly labeled -- this isn't a guess, it's the same account's own on-file name.
- **Data-quality guardrail**: a match is only accepted as "the only account worldwide with this name" when that account has *no* location on file (an unclaimed/unconfirmed profile). If the only same-name account has a confirmed address somewhere clearly unrelated (a different country or a distant state), that's treated as evidence *against* a match, not neutral -- it's left as not found.
- **How hard "not found" was actually tried**: the original ~85 unmatched players (from the current 2-week window) went through six separate passes: (1) nickname/hyphen/word-order variants, (2) a worldwide (not just Texas) search radius, (3) rare-surname isolation, (4) mining every account that changed its display name across the ~70 scrapes (this is what resolved "SR T" → "Raj T" and "Lacie henry" → "Lacie Petsch" -- verified by checking the account showed a single clean rename cutover on one scrape date, not two names alternating, before trusting it), (5) a top-up pass with transliteration variants, swapped name order, vowel-drops, and surname/first-name-alone queries, and (6) a final completeness audit that mechanically counted every prior attempt per name and topped each one up with typo-transposition and alternate-spelling queries until it hit 10 distinct searches -- or, for the handful of names too short to generate 10 meaningfully different queries (bare initials, single tokens), until no further distinct variant existed to try. A DUPR club-roster cross-reference, a plain web search, a "Lastname, Firstname" comma-format test, and an empty-query browse attempt were also tried and came up empty (no registered DUPR club for Apex Pickleball Clubs Cedar Park; the search API requires a non-empty query and doesn't parse comma format). After all of that, the remaining unmatched break down into: players with only initials on file (no technique can recover an identity from two letters), players confirmed absent from DUPR (zero hits worldwide even on their most distinctive name fragment), a few "family cluster" cases where a relative with the same rare surname plays locally but the specific person doesn't (not treated as a match), and common-name collisions with no standout candidate.
- **Decision to stop here**: after that full effort, the club owner reviewed the options (close it out / show unconfirmed weak candidates anyway / supply specifics for individual names) and chose to close it out at this count rather than list unconfirmed guesses. The 81 unmatched players are the final state, not a gap left for lack of trying.

## Summary

- **520** unique players appear across the full scrape history with a numeric Apex rating on file.

- **288** were matched to a DUPR account with a numeric doubles rating -- this is the chartable set.

- **65** matched a DUPR account, but that account has no doubles rating yet (`NR`).

- **167** had no findable DUPR account near Austin, even after multiple retry passes.

## Full player table

Sorted by number of Apex sessions attended across all of history (most active first). Reliability is DUPR's own 0-100 confidence score for that rating. A [CSV export](player-level-vs-dupr.csv) with the same data (plus not-found rows) is also available.

| Player | Sessions | Apex level | DUPR name | DUPR ID | Location | DUPR doubles | Doubles reliability | DUPR singles | Singles reliability | Last DUPR game | Confidence | Notes |
|---|---:|---|---|---|---|---:|---:|---:|---:|---|---|---|
| Lalla Cox | 36 | 2+ | Lalla Cox | Q594V5 | Cedar Park, TX, US | 3.119 | 50 | — | 0 | 2025-12-07 | high | single Austin-metro match |
| Karen Ki | 20 | 2 | Karen Kim | V6O5P7 | Austin, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Suraphat Sricha | 20 | 4 | suraphat sricha | YGLRO4 | Austin, TX, US | 3.598 | 50 | 3.28 | 10 | 2025-10-25 | high | single Austin-metro match |
| Milan Agarwal | 19 | 4 | Milan Agarwal | 4V65WK | Leander, TX, US | 2.956 | 90 | 3.105 | 30 | 2026-05-18 | high | single Austin-metro match |
| David Pierce | 18 | 2 | David Pierce | VXW207 | Cedar Park, TX, US | 3.038 | 100 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Steven Ungar | 18 | 4 | Steven Ungar | 2QQKP7 | Austin, TX, US | — | — | — | — | — | low | ambiguous among 2 Austin-metro candidates (no ratings to tie-break), picked nearest |
| Mauricio  Contreras | 18 | 2+ | Mauricio  Contreras | ORPQEP | Austin, TX, US | — | — | — | — | — | medium | single Austin-metro match (via variant 'Mauricio Contreras') |
| Keith Frobish | 18 | 2+ | Keith  Frobish | N5DWK2 | Austin, TX, US | 2 | 30 | — | 0 | 2026-06-28 | high | single Austin-metro match |
| Rick Epstein | 17 | 2+ | Rick Epstein | OW7OVP | Austin, TX, US | 2.661 | 1 | — | 0 | 2025-12-21 | high | single Austin-metro match |
| Jody  Drumm | 17 | 1+ | Jody Drumm | NNRMMN | Austin, TX, US | — | — | — | — | — | medium | single Austin-metro match (via variant 'Jody Drumm') |
| Murali Sithuraj | 17 | 3+ | Murali  Sithuraj | ZDZG4W | Austin, TX, US | — | — | — | — | 2026-01-07 | high | single Austin-metro match |
| Agent Art Ofiaza | 16 | 2+ | Arthur Ofiaza | YM46KP | Austin, TX, US | 3.337 | 10 | 3.293 | 30 | 2026-04-25 | medium | single Austin-metro match (via variant 'Art Ofiaza') |
| Hari R | 16 | 3+ | Hari R | DYJJLM | Travis County, TX, US | — | — | — | — | 2026-01-07 | low | single Austin-metro match; original name had a bare initial, treat match as uncertain |
| Ronnie S | 15 | 2+ | ronnie sng | 4VNRQK | Austin, TX, US | 2.033 | 10 | — | 0 | 2025-07-12 | low | single Austin-metro match; original name had a bare initial, treat match as uncertain |
| Scotty Sharpe | 15 | 5 | Scotty Sharpe | 89RDYV | Cedar Park, TX, US | 4.757 | 30 | — | 0 | 2025-10-25 | high | single Austin-metro match |
| Evan Tran | 14 | 4 | Evan Transue | 17PMP5 | Austin, TX, US | 4.202 | 30 | 3.542 | 10 | 2025-06-07 | medium | tie-break among 2 Austin-metro candidates by rating |
| Avinash Bhandari | 14 | 4 | Avinash Bhandari | ZDL6NW | — | 3.701 | 10 | — | 0 | 2026-06-04 | medium | tie-break among 2 Austin-metro candidates by rating |
| Captain Kyle Dunn | 14 | 3 | Kyle Dunn | 6PW6DD | Leander, TX, US | 2.923 | 50 | — | 0 | 2026-06-28 | medium | single Austin-metro match (via variant 'Kyle Dunn') |
| Steven Stone | 14 | 3 | Steven Stone | JJGV5O | Leander, TX, US | 2.783 | 100 | — | 0 | 2026-06-14 | high | single Austin-metro match |
| Bridget Clark | 14 | 2+ | Bridget Clark | X0RWWX | Georgetown, TX, US | 3.3 | 90 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Aida Veiga | 14 | 3 | Aida Barbosa Veiga | W6KGMK | Cedar Park, TX, US | 3.376 | 50 | — | 0 | 2026-04-26 | high | single Austin-metro match |
| Julie Jasiota | 13 | 2 | Julie Jasiota | D9NLKM | Pflugerville, TX, US | 2.232 | 10 | — | 0 | 2025-03-24 | high | single Austin-metro match |
| Keith Higbee | 13 | 2 | Keith Higbee | W672LY | — | 2.865 | 1 | — | 0 | 2023-10-18 | low | only DUPR account worldwide with this exact name; location unconfirmed |
| Clark Bruce | 13 | 3 | Clark Bruce | V2GJ9J | Cedar Park, TX, US | — | — | — | — | — | low | ambiguous among 2 Austin-metro candidates (no ratings to tie-break), picked nearest |
| Venkat Raavi | 13 | 5 | Venkata Raavi | 76OJX4 | Leander, TX, US | 4.225 | 100 | — | 0 | 2026-02-18 | high | single Austin-metro match |
| David Cardona | 13 | 3+ | David Cardona | MPLQ5G | Leander, TX, US | 3.282 | 40 | — | 0 | 2026-06-28 | high | single Austin-metro match |
| Noah Wilkerson | 13 | 5 | Noah Wilkerson | 6N5ZMD | — | 4.676 | 100 | 3.95 | 60 | 2026-06-06 | high | single Austin-metro match |
| Art Irwin | 12 | 2+ | Art Irwin | KZ42ZY | Cedar Park, TX, US | 2.634 | 50 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Jennifer Dunn | 12 | 2 | Jennifer Dunn | 4Q9E5M | Cedar Park, TX, US | 2.803 | 20 | — | 0 | 2026-04-26 | high | single Austin-metro match |
| Udit D | 12 | 3+ | Udit Dadwani | 9959YR | Austin, TX, US | 2.919 | 60 | — | 0 | 2025-12-20 | low | tie-break among 2 Austin-metro candidates by rating; original name had a bare initial, treat match as uncertain |
| Advay Raju | 12 | 3+ | Advay Raju | WKR4JY | Cedar Park, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Josh Gleich | 11 | 4 | Josh Gleich | 3VW56J | Austin, TX, US | 3.774 | 100 | 3.789 | 10 | 2026-07-14 | high | single Austin-metro match |
| Christine  OLeary | 11 | 3 | Christine OLeary | L5YZN5 | Austin, TX, US | 3.273 | 30 | — | 0 | 2025-07-09 | medium | single Austin-metro match (via variant 'Christine OLeary') |
| Dan Tran | 11 | 3 | Dan Tran | V2L9D7 | Austin, TX, US | 3.203 | 70 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Gerard Bravo | 11 | 2+ | Gerard Bravo | 4VK6L2 | Leander, TX, US | 3.035 | 100 | — | 0 | 2026-06-28 | high | single Austin-metro match |
| Rick Larrea | 11 | 3+ | Rick Larrea | Z9OZVM | Austin, TX, US | 3.361 | 30 | — | 0 | 2024-12-01 | high | single Austin-metro match |
| Keylan Haynes | 11 | 2 | Keylan Haynes | YMKNGG | Austin, TX, US | 2.415 | 70 | — | 0 | 2026-05-17 | high | single Austin-metro match |
| Levy Saldana | 11 | 2 | levy Saldana | X025R4 | Cedar Park, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Brian McLeroy | 11 | 3 | Brian  McLeroy | 2QMRW7 | Cedar Park, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Ling-Yu Kan | 10 | 2 | Ling-Yu Kan | GWLWPQ | Cedar Park, TX, US | 2.484 | 70 | — | 0 | 2026-05-22 | high | single Austin-metro match |
| Sue Whieldon | 10 | 3+ | Sue Whieldon | YGWP6D | Leander, TX, US | 3.759 | 60 | — | 0 | 2026-04-26 | high | single Austin-metro match |
| Christine McCully | 10 | 3 | Christine  McCully | WZRN5G | Cedar Park, TX, US | 2.361 | 10 | — | 0 | 2026-05-16 | high | single Austin-metro match |
| Dennis Porter | 10 | 4 | Dennis Porter | ZNVZ4P | Cedar Park, TX, US | 3.242 | 100 | 3.25 | 60 | 2026-07-18 | high | single Austin-metro match |
| Chris Wiles Wiles | 10 | 3+ | Christopher Wiles | NRYG52 | Cedar Park, TX, US | 3.351 | 100 | 3.799 | 1 | 2026-07-11 | high | DUPR excludes your own logged-in account from search results; filled in directly from your profile page. |
| Ravi Sherom | 10 | 3+ | Ravi Sheromani | XON7D4 | Leander, TX, US | 3.282 | 40 | — | 0 | 2026-06-28 | high | single Austin-metro match |
| Marion Serelis | 10 | 2 | Marion Serelis | VXXNV7 | Austin, TX, US | 2.331 | 90 | — | 0 | 2026-04-29 | high | single Austin-metro match |
| Penny Goh | 10 | 2 | Penny Goh | J5NQ74 | Williamson County, TX, US | 2.23 | 1 | — | 0 | 2025-09-06 | high | single Austin-metro match |
| Ryan Church | 10 | 2 | Ryan Church | 6N9XV0 | Leander, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Justin Ly | 10 | 1+ | Justin Ly | G7WDXG | Cedar Park, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Elly Heber | 10 | 2+ | elly heber | YXO07G | Williamson County, TX, US | 3.125 | 100 | — | 0 | 2026-06-22 | high | single Austin-metro match |
| Mike Yeh | 10 | 5 | Mike Yeh | YNPK9P | — | 3.426 | 100 | — | 0 | 2026-07-18 | high | single Austin-metro match |
| Bojidar (Buddy) Kraptchev | 9 | 2+ | Bojidar Kraptchev | X0DZ95 | Austin, TX, US | 2.863 | 30 | — | 0 | 2026-06-28 | medium | single Austin-metro match (via variant 'Bojidar Kraptchev') |
| Y Lu | 9 | 2 | Yvonne Lu | RZP9WZ | Austin, TX, US | 2.787 | 1 | — | 0 | 2024-07-28 | medium | tie-break among 4 Austin-metro candidates by rating |
| Alexandra Klose | 9 | 2 | Alexandra Klose | 7ZP0D9 | Leander, TX, US | 2.792 | 60 | — | 0 | 2026-07-18 | high | single Austin-metro match |
| Melissa Yeilding | 9 | 3+ | Melissa Yeilding | 94DZVR | Cedar Park, TX, US | 3.416 | 30 | — | 0 | 2025-08-24 | high | single Austin-metro match |
| David Richter | 9 | 3 | David Richter | 0RZ2JQ | — | — | — | — | — | — | low | only DUPR account worldwide with this exact name; location unconfirmed |
| AJ Mitchell | 9 | 2+ | AJ Mitchell | 6KY26G | Leander, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Julia Hall | 9 | 1+ | Julia Scariot Haller | EWQWYM | Austin, TX, US | 3.005 | 100 | — | 0 | 2026-07-14 | high | single Austin-metro match |
| Lauren Konogeris | 9 | 3 | Lauren Konogeris | 990Q2E | Georgetown, TX, US | 3.294 | 100 | — | 0 | 2026-07-13 | high | single Austin-metro match |
| Pam Williamson | 9 | 2 | Pam  Williamson | L2ZQR6 | Cedar Park, TX, US | 2.592 | 100 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Aravindan Ponnuswamy | 9 | 3+ | Aravindan Ponnuswamy | NRDVX6 | Leander, TX, US | 3.629 | 10 | — | 0 | 2025-12-06 | high | single Austin-metro match |
| Sunny Rathore | 9 | 5 | sunny Rathore | L2W9ZQ | Williamson County, TX, US | 4.097 | 60 | — | 0 | 2026-04-25 | high | single Austin-metro match |
| Liz Divelbiss | 9 | 2 | Elizabeth  Divelbiss | G0LLQG | Austin, TX, US | 2.226 | 20 | — | 0 | 2025-09-16 | medium | single Austin-metro match (via variant 'Elizabeth Divelbiss') |
| Sonny Vongtip | 8 | 3+ | Sonny  Vongtip | K5OMW7 | Cedar Park, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Lionel LeBlanc | 8 | 2 | Lionel LeBlanc | DNQDGL | Leander, TX, US | 2.735 | 40 | — | 0 | 2025-08-03 | high | single Austin-metro match |
| Cheryl Mulloy | 8 | 3 | Cheryl Mulloy | ZNV06W | Leander, TX, US | 3.078 | 100 | — | 0 | 2026-06-14 | high | single Austin-metro match |
| Byron Williams | 8 | 3 | Byron Williams | EG9VXW | Austin, TX, US | 3.221 | 30 | — | 0 | 2024-08-15 | high | single Austin-metro match |
| K Madras | 8 | 2+ | Karthik Madras | V6RXEE | Austin, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Harold Arias | 8 | 4 | Harold Arias | MP5VYO | Cedar Park, TX, US | 3.686 | 20 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Peyton Tran | 8 | 4 | Peyton Tran | NX0GEZ | Austin, TX, US | 3.116 | 20 | — | 0 | 2026-06-28 | high | single Austin-metro match |
| Glen Reilly | 8 | 2+ | Glen Reilly | YX4GPG | Georgetown, TX, US | 3.224 | 60 | 3.294 | 10 | 2025-08-28 | high | single Austin-metro match |
| Brittany Browning | 8 | 3+ | Brittany Browning | YXO06D | — | 3.212 | 90 | — | 0 | 2026-04-25 | high | single Austin-metro match |
| Dimitri  Poulis | 8 | 5 | Dimitris Poulis | 2YYEGY | Leander, TX, US | 4.522 | 100 | — | 0 | 2026-06-14 | medium | single Austin-metro match (via variant 'Dimitri Poulis') |
| Eddie Torres | 8 | 3 | Eddie Torres | 6ZZWN0 | Cedar Park, TX, US | 4.302 | 10 | — | 0 | 2025-03-11 | high | single Austin-metro match |
| Brian Lawrence | 8 | 4 | Brian Lawrence | E9Q52M | Liberty Hill, TX, US | 3.678 | 40 | — | 0 | 2026-06-28 | high | single Austin-metro match |
| Scott Shoultz | 8 | 3+ | Scott  Shoultz | V62K97 | Austin, TX, US | 2.638 | 90 | — | 0 | 2026-07-06 | high | single Austin-metro match |
| Leo Toupin | 8 | 3 | Leo Toupin | KOVGGQ | Austin, TX, US | — | — | — | — | — | high | single Austin-metro match |
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
| Akhil M | 7 | 1+ | Akhil Mishra | 4LZ492 | Austin, TX, US | 3.928 | 100 | 3.678 | 30 | 2026-07-14 | low | tie-break among 2 Austin-metro candidates by rating; original name had a bare initial, treat match as uncertain |
| Amanda Erbstoesser | 7 | 4 | Amanda Erbstoesser | G5W26V | Cedar Park, TX, US | 3.746 | 90 | — | 0 | 2026-05-18 | high | single Austin-metro match |
| Mark LeBaron | 7 | 3 | Mark LeBaron | GXGZMQ | Leander, TX, US | 3.054 | 70 | — | 0 | 2026-06-27 | high | single Austin-metro match |
| Steve Sharp | 7 | 3+ | Steve Sharp | 4PKXZV | Austin, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Justin Zielecki | 7 | 2 | Justin Lozano-Zielecki | G0KX2D | Cedar Park, TX, US | 2.806 | 1 | — | 0 | 2025-08-23 | high | single Austin-metro match |
| Nicholas Delbar | 7 | 3 | Nicholas Delbar | RYMWMQ | Cedar Park, TX, US | 3.121 | 10 | 3.06 | 20 | 2025-08-02 | high | single Austin-metro match |
| Hunter Gray | 7 | 4 | Hunter Gray | 6ZDJ40 | Cedar Park, TX, US | 4.043 | 10 | 3.177 | 1 | 2025-07-25 | high | single Austin-metro match |
| SR T | 6 | 4+ | Raj T | V295VP | Austin, TX, US | 2.527 | 10 | — | 0 | 2026-07-13 | high | resolved via roster history: this Apex account's display name changed between snapshots -- it shows as 'Raj T' in 52 historical event rosters and 'SR T' in 15, same underlying player ID -- and 'Raj T' is an exact DUPR match, 17mi away in Austin. |
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
| Derik  LeBaron | 6 | 3 | Derik  LeBaron | 2PWZO7 | Georgetown, TX, US | 3.132 | 50 | — | 0 | 2026-06-27 | medium | single Austin-metro match (via variant 'Derik LeBaron') |
| Elizabeth Steiner | 6 | 2 | Elizabeth Steiner | KY6LYQ | Austin, TX, US | 2.873 | 80 | — | 0 | 2026-05-23 | high | single Austin-metro match |
| Rebecca  Garcia | 6 | 2 | Rebecca Garcia | 55YMDV | — | 2.219 | 100 | — | 0 | 2026-07-14 | medium | single Austin-metro match (via variant 'Rebecca Garcia') |
| Allen  Dees | 6 | 2 | Allen R Dees | 9PE7NR | Cedar Park, TX, US | 3.123 | 80 | — | 0 | 2026-06-14 | medium | single Austin-metro match (via variant 'Allen Dees') |
| Lucas Henriques | 6 | 4+ | Lucas Barbosa Henriques | 304W74 | Cedar Park, TX, US | 3.911 | 90 | — | 0 | 2026-06-29 | high | single Austin-metro match |
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
| teri olaughlin | 5 | 3 | teri olaughlin | WK7J0Y | Cedar Park, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Gayla Clark | 5 | 3 | Gayla Clark | 6Z6E0D | Austin, TX, US | 3.307 | 100 | — | 0 | 2026-06-28 | high | single Austin-metro match |
| Kristie Tyson | 5 | 2 | Kristie Tyson | XJRY6R | Austin, TX, US | 3.138 | 100 | — | 0 | 2026-07-13 | high | single Austin-metro match |
| Aneesh V | 5 | 5 | Aneesh Venkataraman | 2YPY5Y | Cedar Park, TX, US | — | — | — | — | — | low | single Austin-metro match; original name had a bare initial, treat match as uncertain |
| Mark Speich | 5 | 2 | Mark Speich | WKNP2G | — | — | — | — | — | — | low | only DUPR account worldwide with this exact name; location unconfirmed |
| Barbara Johnson | 5 | 2 | Barbara Johnson | GXW75G | Austin, TX, US | 2 | 60 | — | 0 | 2026-04-04 | high | single Austin-metro match |
| Yuni Delancy | 5 | 2+ | Yuni Delancy | LVZNW5 | Cedar Park, TX, US | 2.474 | 70 | — | 0 | 2026-04-27 | high | single Austin-metro match |
| Max Crites | 5 | 4+ | max Crites | YMGW6E | Leander, TX, US | — | 0 | 4.152 | 1 | 2025-09-20 | high | single Austin-metro match |
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
| Lynette Dimbero | 4 | 1+ | Lynette  Dimbero | 4PV25K | Williamson County, TX, US | 2.067 | 60 | — | 0 | 2025-11-16 | high | single Austin-metro match |
| Stephanie Doherty | 4 | 3+ | Stephanie Doherty | NYRDPN | Round Rock, TX, US | 3.206 | 50 | — | 0 | 2025-09-17 | high | single Austin-metro match |
| Jennifer Toupin | 4 | 1+ | Jennifer Toupin | 55P2DL | Austin, TX, US | 2.488 | 100 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Heidi Hopper | 4 | 1+ | Heidi Hopper | KZD50Y | Cedar Park, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Tom Eaton | 4 | 3 | Tom Eaton | V770LE | Austin, TX, US | 3.087 | 60 | — | 0 | 2026-02-01 | high | single Austin-metro match |
| Amanda Niemann | 4 | 2 | Amanda Niemann | M25JMD | Round Rock, TX, US | 2.384 | 100 | — | 0 | 2026-07-14 | high | single Austin-metro match |
| Terri Schulz | 4 | 2 | Terri Schulz | O6OZJ7 | Round Rock, TX, US | 2.49 | 80 | — | 0 | 2026-05-22 | high | single Austin-metro match |
| Daniel hyam | 4 | 3 | Daniel Hyam | ORYKDL | Austin, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Julia Nickerson | 4 | 2 | Julia Nickerson | GWV4OG | Travis County, TX, US | 3.88 | 1 | — | 0 | 2026-06-21 | high | single Austin-metro match |
| Diego Quezada | 4 | 4 | Diego Quezada | L29Q5J | Austin, TX, US | 3.691 | 60 | — | 0 | 2026-05-17 | high | single Austin-metro match |
| Michael Uebel | 4 | 2 | Michael Uebel | E96DQV | Leander, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Bharat Kallem | 4 | 2 | Bharat Kallem | 4QJ5LK | Leander, TX, US | 2.482 | 10 | — | 0 | 2026-06-15 | high | single Austin-metro match |
| Jafet Salty | 4 | 3+ | Jafet Salty | 7D7DK9 | Leander, TX, US | 3.687 | 100 | 3.365 | 10 | 2026-07-11 | high | single Austin-metro match |
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
| Noah Welker | 3 | 4+ | Noah  Welker | RW4QMM | Lubbock, TX, US | 4.276 | 20 | 4.603 | 30 | 2026-02-20 | low | recovered on a second, deeper retry: only exact-name match found anywhere; it's far from Austin (Lubbock, TX, ~5hr away), so treat as uncertain -- no closer or more plausible candidate exists though |
| Austin Steadman | 3 | 4+ | Austin Steadman | GG5REG | Leander, TX, US | 3.769 | 100 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Bryson Renouard | 3 | 5 | Bryson Renouard | O6ELLP | Austin, TX, US | 3.835 | 70 | 3.6 | 40 | 2026-02-01 | high | single Austin-metro match |
| TUNG GIANG | 3 | 5 | Tung Giang | XJNEZR | Cedar Park, TX, US | 4.133 | 1 | — | 0 | 2025-02-03 | high | single Austin-metro match |
| Patty Jistel | 3 | 2+ | Patty Jistel | 7ZWOQ4 | Austin, TX, US | 3.023 | 90 | — | 0 | 2026-05-22 | high | single Austin-metro match |
| Sherry Winn | 3 | 2 | Sherry Winn | V20NZJ | Leander, TX, US | 2.058 | 100 | — | 0 | 2026-05-04 | high | single Austin-metro match |
| Nicole Bell | 3 | 3+ | Nicole Bell | ZDZGVL | Georgetown, TX, US | 3.4 | 100 | — | 0 | 2026-04-25 | high | single Austin-metro match |
| Carla Carrasco | 3 | 2 | Carla Carrasco | Q5NWL0 | Austin, TX, US | 2.645 | 70 | — | 0 | 2026-04-11 | high | single Austin-metro match |
| Erin Price | 3 | 1+ | Erin Price | 8K2VO6 | Cedar Park, TX, US | 2.282 | 30 | — | 0 | 2025-08-31 | high | single Austin-metro match |
| Jorge Taboada | 3 | 3+ | Jorge Taboada | 8MQR6G | Austin, TX, US | 3.659 | 80 | 3.706 | 30 | 2026-07-11 | high | single Austin-metro match |
| Lacie henry | 3 | 2 | Lacie Petsch | RWL9WM | Georgetown, TX, US | 2.454 | 90 | — | 0 | 2026-07-14 | high | resolved via roster history: this Apex account's display name changed between snapshots -- it shows as 'Lacie Petsch' in 44 historical event rosters and 'Lacie henry' in 20, same underlying player ID -- and 'Lacie Petsch' is an exact DUPR match, 12mi away in Georgetown. |
| Tim Moore | 3 | 4 | Tim Moore | Z9676D | Round Rock, TX, US | 3.488 | 30 | — | 0 | 2025-04-22 | high | single Austin-metro match |
| Vonda Ilseng | 3 | 2 | Vonda Ilseng | VX6REP | Cedar Park, TX, US | 2.762 | 90 | — | 0 | 2026-07-12 | high | single Austin-metro match |
| Mohammed Abdelkafi | 3 | 3 | Mohammed Abdelkafi | EXKEDE | Austin, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Sunil Ramachandra | 3 | 2 | Sunil Ramachandra | DYYZZL | Cedar Park, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Ruthie Reyes | 3 | 1+ | Ruthie Reyes | 8D9O63 | Cedar Park, TX, US | 2.497 | 30 | — | 0 | 2025-07-13 | high | single Austin-metro match |
| Ananth Varshith Yelamanchili | 3 | 2 | Ananth Varshith Yelamanchili | G0D76X | Austin, TX, US | 2.657 | 100 | — | 0 | 2026-07-13 | high | single Austin-metro match |
| Sandeep Prabhu | 3 | 1B | Sandeep Prabhu | KD5W4K | — | — | — | — | — | — | low | only DUPR account worldwide with this exact name; location unconfirmed |
| Ronit Mukerji | 3 | 4 | Ronit Mukerji | 8W7G5Y | Austin, TX, US | 4.011 | 100 | 4.295 | 60 | 2026-05-02 | high | single Austin-metro match |
| Nam Nguyen | 3 | 5 | Nam Nguyen | 3ZQ70P | Austin, TX, US | 4.124 | 100 | 3.934 | 10 | 2026-04-07 | medium | tie-break among 3 Austin-metro candidates by rating |
| Rajesh Yarlagadda | 3 | 3 | Rajesh Yarlagadda | 0Z4G4N | Austin, TX, US | 3.325 | 100 | 3.418 | 100 | 2026-07-18 | high | single Austin-metro match |
| Vasu K | 3 | 3 | Vasu Kadalagere | E9DLNW | Cedar Park, TX, US | — | — | — | — | — | low | single Austin-metro match; original name had a bare initial, treat match as uncertain |
| Vince Zanella | 3 | 4 | Vince Zanella | 59D24R | Austin, TX, US | 3.503 | 50 | — | 0 | 2026-06-28 | high | single Austin-metro match |
| Chien Chen | 3 | 2 | Chien Chen | V7K64J | — | 3.407 | 40 | — | 0 | 2025-11-12 | high | single Austin-metro match |
| Richard Lazarus | 3 | 2 | Richard Lazarus | 16MJ4K | Cedar Park, TX, US | 2.695 | 1 | — | 0 | 2025-01-12 | high | single Austin-metro match |
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
| Robin Latham | 2 | 1+ | Robin Latham | 2QKL29 | Williamson County, TX, US | 2.365 | 100 | — | 0 | 2026-07-05 | high | single Austin-metro match |
| Gordon Makely | 2 | 3 | Gordon Makely | KOJKV7 | Leander, TX, US | 2.882 | 100 | — | 0 | 2026-07-19 | high | single Austin-metro match |
| Paula Williams | 2 | 2 | Paula Williams | PK7QWZ | Cedar Park, TX, US | 2.456 | 90 | — | 0 | 2026-04-19 | high | single Austin-metro match |
| Sarah Voight | 2 | 2 | Sarah  Voight | YXW7DE | Leander, TX, US | 2.289 | 100 | — | 0 | 2026-06-27 | high | single Austin-metro match |
| Danielle Rios | 2 | 5 | Danielle Rios | YXE4O4 | Austin, TX, US | 4.512 | 100 | — | 0 | 2026-06-13 | high | single Austin-metro match |
| Paul Bedeski | 2 | 4 | Paul Bedeski | WX2MGM | Austin, TX, US | 3.336 | 60 | — | 0 | 2025-08-24 | high | single Austin-metro match |
| Matt Gibson | 2 | 4 | Matt Gibson | N7DZKN | Austin, TX, US | 3.968 | 70 | — | 0 | 2026-04-27 | medium | tie-break among 2 Austin-metro candidates by rating |
| Yash Bhagat | 2 | 2 | Yash Bhagat | EVXEDV | Cedar Park, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Stacy Wheetley | 2 | 4 | Stacy Wheetley | 8KKWD7 | Austin, TX, US | 4.137 | 100 | — | 0 | 2026-05-31 | high | single Austin-metro match |
| Allie Paul | 2 | 1+ | Allie Paul | E96VMM | Georgetown, TX, US | 2.938 | 1 | — | 0 | 2025-04-14 | high | single Austin-metro match |
| Robin Petty | 2 | 1+ | Robin Petty | ELXMPJ | TX, US | 2.558 | 1 | — | 0 | 2025-10-04 | low | only DUPR account worldwide with this exact name; location unconfirmed |
| Kensley Fort | 2 | 4 | Kensley Fort | G5OKQG | Austin, TX, US | 3.508 | 100 | 3.855 | 100 | 2026-07-14 | high | single Austin-metro match |
| Jeff Brabant | 2 | 4 | Jeff Brabant | 3VG9EP | Austin, TX, US | 4.585 | 30 | — | 0 | 2023-11-08 | high | single Austin-metro match |
| Rohit  Goel | 2 | 2+ | Rohit Goel | 2Z9EJ4 | Austin, TX, US | — | — | — | — | — | medium | single Austin-metro match (via variant 'Rohit Goel') |
| Manny Garcia | 2 | 4 | Manny Garcia | YGW4QP | Austin, TX, US | 4.099 | 70 | 3.121 | 10 | 2026-04-26 | high | single Austin-metro match |
| Justin Ojemi | 2 | 4 | Justin Ojemi | PKLENE | Houston, TX, US | 4.054 | 100 | — | 0 | 2026-07-07 | low | only DUPR account worldwide with this exact name; location unconfirmed |
| Natalie Hannah | 2 | 0.9 (between L1B and L1+) | Natalie Hannah | 99Y59V | — | 2.546 | 1 | — | 0 | 2024-03-16 | low | only DUPR account worldwide with this exact name; location unconfirmed |
| Dana Turner | 1 | 2 | Dana Turner | MEVRZV | Austin, TX, US | 2.381 | 20 | — | 0 | 2026-02-08 | high | single Austin-metro match |
| Logan  Turner | 1 | 2 | Logan Turner | 4EVRKG | Austin, TX, US | — | — | — | — | — | medium | single Austin-metro match (via variant 'Logan Turner') |
| Mark Mumaw | 1 | 2 | Mark Mumaw | 6765MK | Austin, TX, US | 2.635 | 100 | 2.613 | 10 | 2026-05-04 | high | single Austin-metro match |
| Nazir Siddiqi | 1 | 3+ | Nazir  Siddiqi | RXRJPD | Cedar Park, TX, US | 2.97 | 60 | — | 0 | 2025-10-24 | high | single Austin-metro match |
| John Cogdell | 1 | 3+ | John Cogdell | 76ZZ24 | Austin, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Ling Wang | 1 | 4 | Ling Wang | KXP60Q | Austin, TX, US | 3.636 | 1 | 3.317 | 10 | 2025-02-16 | high | single Austin-metro match |
| Kristy Cravey | 1 | 2 | Kristy Cravey | Z9RXMM | — | 2.629 | 1 | — | 0 | 2024-04-04 | low | only DUPR account worldwide with this exact name; location unconfirmed |
| Adrian  Godoy | 1 | 2 | Adrian Godoy | 4Q60KK | Leander, TX, US | 2.738 | 70 | 2.194 | 30 | 2026-07-18 | medium | single Austin-metro match (via variant 'Adrian Godoy') |
| Sandy  Ross | 1 | 2 | Sandy Ross | VXZ0G5 | Cedar Park, TX, US | 2.943 | 90 | — | 0 | 2026-05-11 | medium | single Austin-metro match (via variant 'Sandy Ross') |
| Steven Smith | 1 | 3 | Steve Smith | W6V6JL | Austin, TX, US | — | — | — | — | — | low | recovered on a second, deeper retry: closest candidate by far (17mi) among many same-name matches worldwide, but the account has no rated doubles/singles yet and 'Smith' is too common to be fully certain |
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
| Stephanie Aromy | 1 | 2 | Stephanie Aromy | 7D4VQM | Lago Vista, TX, US | 2.748 | 100 | — | 0 | 2026-05-14 | high | single Austin-metro match |
| Chrissy Hicks | 1 | 2 | Chrissy Hicks | 2LO699 | Liberty Hill, TX, US | 2.449 | 100 | — | 0 | 2026-05-14 | high | single Austin-metro match |
| Erin Brotherman | 1 | 2 | Erin Brotherman | 0QX4JN | Georgetown, TX, US | 2.851 | 100 | — | 0 | 2026-06-23 | high | single Austin-metro match |
| Adil Dhanani | 1 | 3 | Adil Dhanani | M2XK4D | Round Rock, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Lisa Gutierrez | 1 | 2 | Lisa Gutierrez | X27V07 | Austin, TX, US | 2.411 | 100 | — | 0 | 2026-05-09 | high | single Austin-metro match |
| Shane Chen | 1 | 4 | Shane Chen | V42E9E | Williamson County, TX, US | 3.072 | 100 | — | 0 | 2026-05-17 | high | single Austin-metro match |
| Jieli Wei | 1 | 3 | Jieli Wei | EWLQRJ | Austin, TX, US | 3.076 | 100 | — | 0 | 2026-05-17 | high | single Austin-metro match |
| Si Liu | 1 | 2 | Siyu Liu | Q9OPOD | Austin, TX, US | — | — | — | — | — | low | ambiguous among 2 Austin-metro candidates (no ratings to tie-break), picked nearest |
| Elton N | 1 | 2 | Elton Nie | 7J0ZQ0 | Austin, TX, US | 2.977 | 100 | — | 0 | 2026-07-08 | low | single Austin-metro match; original name had a bare initial, treat match as uncertain |
| Jady Cheng | 1 | 2 | jady cheng | JYPJDD | Cedar Park, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Chi Nguyen | 1 | 2 | Chi Nguyen | 8KL6Q3 | Austin, TX, US | 2.055 | 40 | — | 0 | 2025-09-19 | medium | tie-break among 3 Austin-metro candidates by rating |
| Alex Kaplan | 1 | 3 | Alex Kaplan | 3LZJ06 | Austin, TX, US | 4.178 | 30 | — | 0 | 2025-06-03 | high | single Austin-metro match |
| Jeff Wilkinson | 1 | 5 | Jeff Wilkinson | 8K7LY3 | Austin, TX, US | 4.375 | 40 | 3.839 | 30 | 2025-08-23 | high | single Austin-metro match |
| Ash B | 1 | 5 | Asher Bai | 6ZQ72D | Austin, TX, US | 4.56 | 40 | — | 0 | 2026-05-02 | low | tie-break among 5 Austin-metro candidates by rating; original name had a bare initial, treat match as uncertain |
| Michael Griffin | 1 | 3+ | Michael Griffin | 17GGN8 | Austin, TX, US | 2.902 | 80 | — | 0 | 2026-04-16 | high | single Austin-metro match |
| Rey Chapa | 1 | 4+ | Rey Chapa | NYDQRN | Cedar Park, TX, US | 4.185 | 30 | — | 0 | 2025-08-23 | high | single Austin-metro match |
| Carleen Pecaoco | 1 | 2 | carleen Pecaoco | WKQO7L | Leander, TX, US | 2.418 | 100 | — | 0 | 2026-05-14 | high | single Austin-metro match |
| Danielle Duplechain | 1 | 3 | Danielle Duplechain | 4ZO0D6 | Austin, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Olivia Smith | 1 | 3 | Olivia Smith | YNPEMD | Austin, TX, US | 3.353 | 60 | — | 0 | 2026-03-08 | high | single Austin-metro match |
| Drupadh Yalamanchili | 1 | 2 | Drupadh Yalamanchili | 7ZQY9N | Austin, TX, US | 2.674 | 30 | — | 0 | 2026-06-15 | high | single Austin-metro match |
| Nagendra Pavan Anganna | 1 | 2 | Nagendra Pavan Anganna | M9LWNL | Liberty Hill, TX, US | 2.482 | 10 | — | 0 | 2026-06-15 | high | single Austin-metro match |
| Sean Xu | 1 | 2 | Sean  Xu | KYXV57 | US | — | — | — | — | — | high | single Austin-metro match |
| Omer Jaweed | 1 | 0.75 (between L1B and L1+) | OMER Jaweed | OZWMXL | — | — | — | — | — | — | low | only DUPR account worldwide with this exact name; location unconfirmed |
| Tristan Yates | 1 | 4 | Tristan Yates | 7DQW24 | Austin, TX, US | 3.977 | 50 | — | 0 | 2026-02-08 | high | single Austin-metro match |
| Arnav Singh | 1 | 3 | Arnav Singh | Z4NVPP | Leander, TX, US | — | — | — | — | — | high | single Austin-metro match |
| Bernard  Kim | 1 | 5 | Bernard Kim | 8EN7V8 | Austin, TX, US | 4.244 | 30 | — | 0 | 2025-06-21 | medium | single Austin-metro match (via variant 'Bernard Kim') |
| Ashok Ravi | 1 | 2 | Ashok Ravi | 76R654 | Austin, TX, US | 2.969 | 20 | — | 0 | 2025-01-19 | high | single Austin-metro match |
| Joby Baby | 1 | 3+ | Joby Baby | 67NDPD | Cedar Park, TX, US | 3.619 | 100 | — | 0 | 2026-07-18 | high | single Austin-metro match |
| Carlos Hernandez | 1 | 4 | Carlos Hernandez | OWOPYE | Cedar Park, TX, US | 3.593 | 100 | — | 0 | 2026-07-18 | medium | tie-break among 2 Austin-metro candidates by rating |

## Not found on DUPR

| Player | Sessions | Apex level | Notes |
|---|---:|---|---|
| Denis Davydenko | 20 | 1+ | no results found after variants |
| Kimberly Tuttle | 15 | 1B | no results found after variants |
| Edwin Feliciano | 13 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Alet Feliciano | 13 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Rocky E | 13 | 1+ | no results found after variants |
| Naveen Bellam | 13 | 2 | not found near Austin -- the only exact-name match worldwide has a confirmed address far away (Sunnyvale, CA), which is real evidence *against* it being the same person, not neutral like an unclaimed profile with no location on file |
| Steve Felgate | 12 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Robin Felgate | 11 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| John B Mulloy | 11 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Sam Ofiaza | 10 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Daifei Li | 10 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Musa I | 10 | 1+ | no results found after variants |
| Diane Stalwick | 10 | 2 | no results found after variants |
| Josh Walenta | 10 | 1+ | no results found after variants |
| Toni Antov | 9 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Ted Gilkey | 8 | 2+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Adi Gupta | 8 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Juliana Hall | 8 | 1B | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| shashank shekhar | 8 | 1B | no results found after variants |
| Viengdala Luanglath | 8 | 2 | no results found after variants |
| Alex Wilkerson | 8 | 1+ | no results found after variants |
| Olivia S Yang | 7 | 4 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| camilleo . | 7 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Mike Wong | 7 | 3 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Amanda Montero | 7 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Cindy Van | 7 | 1+ | no results found after variants |
| Ning Shaw | 6 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Alfred Zhong | 6 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Matt Hamilton | 6 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Jay Quiocho | 6 | 3 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Harry Rochani | 6 | 3+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Belle Garcia | 6 | 4 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Genie Duvall | 6 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Praveen M | 6 | 3+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Denise  Denicola | 6 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Holly Koehn | 6 | 1+ | no results found after variants |
| Heather Smith | 6 | 1B | no results found after variants |
| Mohi Muhammed | 5 | 2+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Ale Robles | 5 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Tina Williams | 5 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Chet Hamilton | 5 | 3 | no results found after variants |
| Ben Butler | 5 | 3 | no results found after variants |
| Joshua  Taylor | 5 | 2 | no results found after variants |
| Russell Conover | 5 | 2+ | no results found after variants |
| Adan Rivas | 5 | 3 | no results found after variants |
| GULAY AKI | 5 | 1B | no results found after variants |
| Steven Tran | 5 | 3 | no results found after variants |
| Lisa Martin | 5 | 2 | no results found after variants |
| Sonie Golden | 4 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| John Tao | 4 | 3 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Shun Huang | 4 | 4 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Azusa Manabe | 4 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Steve  Lau | 4 | 3 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Bungbone Naugle | 4 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Michael Gibson | 4 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Miguel Mercado | 4 | 3 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Phyllis Cosentino | 4 | 2+ | no results found after variants |
| Baron Bran Mitchell | 4 | 2+ | no results found after variants |
| Isaac Garcia | 4 | 2 | no results found after variants |
| Gino F | 4 | 4 | no results found after variants |
| Nicholas Newell | 4 | 2 | no results found after variants |
| Petra Mora | 4 | 2 | no results found after variants |
| Matt Laakso | 3 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| John McIntyre | 3 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Terra Bowen | 3 | 2 | no results found after variants |
| Ali Smith | 3 | 2 | no results found after variants |
| Amanda Doan | 3 | 2 | no results found after variants |
| Jon Paul Fontenot | 3 | 1+ | no results found after variants |
| Braeden Stubbs | 3 | 1+ | no results found after variants |
| Eli Sherman | 3 | 4 | no results found after variants |
| Kiran Thirvakadu | 3 | 2 | no results found after variants |
| Kirsten Berlin | 3 | 1B | no results found after variants |
| Raissa Carey | 3 | 1+ | no results found after variants |
| Josh Cairns | 3 | 4 | not found near Austin -- the only exact-name match worldwide has a confirmed address far away (Snohomish, WA), which is real evidence *against* it being the same person, not neutral like an unclaimed profile with no location on file |
| Steven Jones | 3 | 4 | no results found after variants |
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
| Mindy Ratcliff | 2 | 1+ | no results found after variants |
| Kharole B | 2 | 3 | no results found after variants |
| Ingrid Evens | 2 | 1B | no results found after variants |
| Katie O'Riley | 2 | 5 | no results found after variants |
| Paul Schulz | 2 | 3 | no results found after variants |
| Kyle Feliciano | 2 | 1+ | no results found after variants |
| Miles Jones | 2 | 2 | no results found after variants |
| Zachary Smith | 2 | 2 | no results found after variants |
| Nhu Nguyen ッ | 2 | 3+ | no results found after variants |
| Tanay Thakkar | 2 | 2 | no results found after variants |
| Javier Larrea | 2 | 2 | no results found after variants |
| Ashley Cavanaugh | 2 | 2 | no results found after variants |
| Leonardo Ladeira | 2 | 2 | no results found after variants |
| Melina Farahi | 2 | 1+ | no results found after variants |
| Jane Ellenberger | 2 | 1+ | no results found after variants |
| Tiffani Herrington | 2 | 1+ | no results found after variants |
| Carol Imperial | 2 | 1+ | no results found after variants |
| Jerry Johnson | 2 | 2 | no results found after variants |
| Teresa Stamper | 2 | 1+ | not found near Austin -- the only exact-name match worldwide has a confirmed address far away (The Villages, FL), which is real evidence *against* it being the same person, not neutral like an unclaimed profile with no location on file |
| Gregory Stamper | 2 | 1+ | no results found after variants |
| Aaron Clough | 2 | 2 | not found near Austin -- the only exact-name match worldwide has a confirmed address far away (West Jordan, UT), which is real evidence *against* it being the same person, not neutral like an unclaimed profile with no location on file |
| Rica Greenwood | 2 | 1+ | no results found after variants |
| Roger Winn | 2 | 1B | no results found after variants |
| Linda Haddox | 2 | 2+ | no results found after variants |
| Clay Crider | 2 | 2 | no results found after variants |
| Kim Phan | 1 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Alexis Gant | 1 | 0.75 (between L1B and L1+) | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| J O | 1 | 1+ | too ambiguous to identify (only initials on file); the closest automatic guess did not actually resemble the name and was dropped on manual review |
| Maxwell Burgess | 1 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Diana Sudduth | 1 | 1+ | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
| Bruce Cong | 1 | 2 | not found on DUPR near Austin, even after trying nickname/hyphen/word-order variants and an extended-radius search |
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
| Scott Ungar | 1 | 3 | no results found after variants |
| Julia Bates | 1 | 3 | no results found after variants |
| Vinh Vuong | 1 | 3+ | no results found after variants |
| Ashwin Venkatram | 1 | 2 | no results found after variants |
| Keith PoonWah | 1 | 2+ | no results found after variants |
| Jose Gutierrez | 1 | 2 | no results found after variants |
| Mike Pucci | 1 | 2 | no results found after variants |
| Robert Grob | 1 | 3 | not found near Austin -- the only exact-name match worldwide has a confirmed address far away (Cincinnati, OH), which is real evidence *against* it being the same person, not neutral like an unclaimed profile with no location on file |
| Taylor Allen | 1 | 1B | no results found after variants |
| McKayla Vega | 1 | 1+ | no results found after variants |
| Jessica Lopez | 1 | 1B | not found near Austin -- the only exact-name match worldwide has a confirmed address far away (Laguna, Philippines), which is real evidence *against* it being the same person, not neutral like an unclaimed profile with no location on file |
| Alma Cardona | 1 | 1B | no results found after variants |
| Zac Jiang | 1 | 2 | no results found after variants |
| thomas peng | 1 | 3 | no results found after variants |
| Alex Ibarra | 1 | 1+ | no results found after variants |
| Aaron Puleski | 1 | 1B | no results found after variants |
| Joshua Puleski | 1 | 1B | no results found after variants |
| Logan Puleski | 1 | 1B | no results found after variants |
| Staceyhl Hirt | 1 | 4 | no results found after variants |
| Anh (Tuan) 💵💵 Nguyen | 1 | 4 | no results found after variants |
| Jack Pirc | 1 | 2+ | no results found after variants |
| Raymond Lindquist | 1 | 3 | no results found after variants |
| Ben Sutter | 1 | 2 | no results found after variants |

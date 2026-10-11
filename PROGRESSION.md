# Progression notes (Ki Duel)

Notes comparing Ki Duel's progression with the reference game in `PROGRESSION-1.png` and `PROGRESSION-2.png`. Nothing here is implemented yet; it's for deciding later what to bring over.

## What the screenshots show

Two party members, Krillin and Gohan, each with their own stats. A shared EXP counter sits top left, and a day counter top right reads "Goku arrives in 6 days".

| Stat | Krillin Lv 2 (shot 1) | Krillin Lv 3 (shot 2) | Gohan Lv 2 (shot 1) | Gohan Lv 4 (shot 2) |
|---|---|---|---|---|
| BP | 1671 | 2075 | 1781 | 2569 |
| HP (current / max) | 485 / 1341 | 1341 / 1502 | 980 / 1080 | 255 / 1586 |
| KI | 6 | 7 | 5 | 13 |
| AP | 166 | 175 | 164 | 197 |
| DP | 77 (+1) | 86 (+1) | 69 (+1) | 83 (+1) |
| SP | 8 | 10 | 9 | 13 |
| CP | 4 | 5 | 4 | 5 |
| BE | 0 | 0 | 0 | 0 |
| EE | 1 | 1 | 0 | 8 |

EXP went from 657 to 1798 between the two shots. The day counter stayed at 6.

## How the stats grow

| Stat | Krillin, Lv 2 → 3 | Gohan, Lv 2 → 4 |
|---|---|---|
| BP | ×1.24 | ×1.44 (about ×1.2 per level) |
| Max HP | +161 | about +250 per level |
| CP | 4 → 5 | 4 → 5 |
| KI | +1 | +8 |
| EE | +0 | +8 |
| AP / DP | +9 / +9 | +33 / +14 |
| SP | +2 | +4 |

## How Ki Duel works today

From `heroStats()`, `xpNeed()` and `SV` in `ki-duel.html`:

- One hero, with XP of their own. Reaching `110 × level^1.5` XP levels up and resets XP to 0.
- BP: `1000 × 1.2^(level − 1)`
- HP: `300 + 70 × (level − 1)`, refilled every battle
- Command slots: `5 + (level − 1)`, up to 12
- Melee bonus and ki bonus: grow from hits landed (`meleeXP`, `energyXP`), up to +50% each
- Special Beam unlocks at level 4
- Progress follows an opponent ladder; there are no days, items or party.

## Comparison

**Matches**
- Level, BP and HP exist in both, and BP is the headline power number.
- BP grows about ×1.2 per level in both. The reference just uses a bigger scale.
- Some growth comes from use, not level. Our melee and ki bonuses grow from hits landed. In the reference, Gohan's KI (5 → 13) and EE (0 → 8) jumped while Krillin's barely moved, even though both levelled. That likely reflects what each of them did in their fights.

**Differences**
1. **Command slots grow much slower there.** If CP is the slot count, the reference has 4 at level 2 and 5 at levels 3 and 4. Ours gives +1 every level, so our level 4 hero has 8 slots where theirs would have 5. This is the biggest gameplay difference for Command Battle.
2. **HP carries over between fights there.** Gohan sits at 255 of 1586 HP. Ours refills every battle. Their max HP also grows proportionally slower (about +12 to 16% per level vs our +23%), but their damage scale differs, so that alone means little.
3. **More visible stats:** KI, AP, DP, SP, CP, BE, EE. Ours folds these into BP plus the two hidden bonuses.
4. **A party of two, each levelling separately.** We have one hero.
5. **EXP looks like a running party total, not something spent.** It rose from 657 to 1798 while both characters levelled. If levelling cost EXP, the number would have dropped.
6. **Items or equipment:** the DP "+1" appears on both characters in both shots.
7. **Time limit:** the "days until Goku" counter instead of a ladder. It didn't change between the shots, so days pass some way other than fighting.

## Open questions

- What do CP, BE and EE mean exactly? The guesses so far: CP is command slots, and EE grows with energy-attack use. BE was 0 for everyone in both shots.
- What makes the days pass, and what happens when they run out?
- Where does the DP "+1" come from?
- Do KI, AP, DP and SP grow from level, from use, or both?
- How does HP get restored if it doesn't refill after a fight?

## Ideas to consider

- Slow the slot growth to match: something like +1 every 2 levels, starting at 4.
- Carry HP over between ladder fights, with some way to heal.
- Show the usage-based bonuses as visible stats, the way the reference shows KI and EE.
- Add a second party member. This would also fit the 2 vs 1 and 2 vs 2 Free Fight formats.

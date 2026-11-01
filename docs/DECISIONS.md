# Battle Emotes Legacy — decision evidence and unresolved choices

**By:** Babuni.

## Direct historical evidence

The first committed `roar.lua` (2025-11-22, `d618976`) explicitly describes the initial addon as based on **BuxbrewCharge**. That is a direct source comment and justifies recording a **technical lineage**, not a claim that AI conceived the original idea.

The README expanded on 2025-11-23 states a clear character-flavor experience: built-in battle emotes chosen randomly from a watched action-bar slot, with adjustable chance/cooldown and an on/off switch. This is repository evidence of the project's stated direction.

## Source-observed technical decisions

| Current approach | Evidence | Qualification |
| --- | --- | --- |
| Built-in emote pool | Five `EMOTE_TOKENS_BATTLE` and `DoEmote` | Built-in client behavior not in-game tested |
| Trigger follows button press | `UseAction` wrapper | Does not inspect cast success |
| Configurable chance and cooldown | `battle_chance`, `BATTLE_COOLDOWN` | Missed roll still consumes cooldown |
| Select a slot without a GUI | `/roarr watch`, `/roarr slot` | Not evidence of a formally rejected GUI |
| Explicitly suspend output | `ENABLED` and `/roarr off/on` | Settings preserved in saved table |
| Account-wide preferences | `SavedVariables: ROARRDB` | Multiple characters may have different slot layouts |
| Rename project in the installed package | November 23 filename and identifier changes | Motivation for repeated renames not known |

## Chronology of visible alternatives

The Git history shows both `roar` and `roarr` names applied to Lua and TOC files, several adjustments within 2025-11-23, a deletion and re-creation sequence, and a final `ROARR` package. The factual sequence is retained; it would be inappropriate to assert that these represent deliberately rejected concepts or that a particular failure forced a rename without logs.

The MIT LICENSE contains `Copyright (c) 2025 Elexior`, while current repo and manifest display Babuni as project author. **Both are preserved**. The historical legal relationship is not verified; no authorship transfer or license edit is implied.

## Creator decisions pending

1. Should chance failures consume a cooldown?
2. Should the saved slot be per-character rather than shared account-wide?
3. Should the two nearly identical ROARR repositories remain separate historical snapshots or eventually share a distribution? Their current source similarity does not settle that creative decision.
4. Should an optional non-public preview be added?
5. Should historical attribution in the LICENSE be clarified?

These questions were **not answered or approved** by Babuni during the documentation expansion.

## 2026-10-26 documentation decision

The assistant expanded docs only. It did not change addon behavior or settle any of the pending choices. Runtime validity remains unverified.

## November 2026 — repository identity

To distinguish its history, I renamed this repository to **BattleEmotesLegacy**. The installed addon continues to use `roarr` filenames, commands and saved variables. The separate `roarr` repository remains a distinct project record. My AI assistant made documentation edits only; no runtime migration was carried out.

## 2026-11-01 — source comparison and guild memories

The `roarr.lua` implementations in this repository and `babunidev/roarr` were compared. Both have the same gameplay logic and settings; only `/roarr tutorial` differs (one compact line here, seven setup steps there). This answers what is currently different, but not why two repositories were kept.

Babuni recalled that the project was associated with the **ROAR guild**. Neither ROARR source contains guild recruiting or invitations. The later **RoarGuild** source implements `/rogu invite`, which manually sends randomized recruitment text to a chat channel, not an actual player invite. No new gameplay behavior or merge was approved.

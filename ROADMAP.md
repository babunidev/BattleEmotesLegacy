# Battle Emotes Legacy — verification and future choices

**By:** Babuni  
**Status:** proposed verification and creator decisions, **not** approved feature work.

## Status and naming

The GitHub repository is **BattleEmotesLegacy**, while the installed addon remains **ROARR**. Any future technical revisions or relationship to the separate `roarr` repository require explicit review; no new gameplay features are approved by this documentation pass.

## Implemented source baseline

- Version 1.0, interface 11200, package `roarr`, slash prefix `/roarr`.
- Five built-in emote tokens: ROAR, CHARGE, CHEER, BORED, FLEX.
- Watched `UseAction` slot with an enabled flag, chance threshold and a `GetTime()` cooldown.
- Defaults: enabled, 100% chance, 6-second interval; account-wide `ROARRDB` saving slot/chance/cooldown/enabled state.
- One Lua file and one TOC; no automated tests in inspected repository tree.

## Priority 1 — prove the existing implementation works

1. Load from a folder named `roarr` on the actual intended 1.12-compatible client; check that slash commands register.
2. Run `/roarr watch`, identify a slot, set it, and confirm the original action continues to work while an emote may trigger.
3. Test 0%, 40% and 100% chance at a manageable cooldown; observe that **a failed chance roll still consumes the cooldown**.
4. Check `/roarr off` / `on` and the tutorial without changing the configured slot.
5. Verify `/reload`, logout/login and preferences on a second character (the TOC declares account-wide data).
6. Test the five built-in tokens on the chosen client and locale; note any emote unavailable on that fork.
7. Test load order alongside other `UseAction` wrappers, particularly related character-emote addons.
8. Test edge cases: negative/invalid slot input, a zero-second cooldown, and a first press shortly after login.
9. Check whether untouched saved settings survive a session in which no action-bar hook or slash command called `ensureLoaded()`.

None of these were executed during this documentation-only session.

## Priority 2 — ask the creator, don't assume

- Should a missed chance roll consume the cooldown, or should the timer start only when an emote actually fires?
- Should slot settings remain account-wide or be character-specific?
- Should the five-token pool stay deliberately small or expand?
- The separate `roarr` repository contains the same gameplay code, with a longer tutorial. Should they remain distinct historical snapshots, or should distribution eventually be consolidated? No merge has been approved.
- Guild-recruitment features belong to **RoarGuild**, not the current Battle Emotes Legacy scope.
- Should the original ROAR-to-ROARR naming history appear as a public-facing portfolio narrative?
- Should the MIT copyright line's relationship to the Babuni author credit be clarified?

Record the creator's explicit answers in `docs/DECISIONS.md` before treating any item as a requirement.

## Release/verification evidence

For each manual test record client build, active addons, steps, expected output, observed output, and commit. Document code fixes in changelog and devlog; don't mark a source inspection as a passed gameplay test.

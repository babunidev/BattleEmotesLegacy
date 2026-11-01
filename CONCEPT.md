# Battle Emotes Legacy — concept and creative direction

**By:** Babuni  
**Package:** `roarr.lua` / `roarr.toc` in `BattleEmotesLegacy` (formerly `roar`).

## The experience

The idea I explored here was to add visible character expression to something I was already doing in-game. The code grew out of the earlier **BuxbrewCharge** pattern, according to its original source comment. By my choice, the historical repository is now named **Battle Emotes Legacy**. Its installed addon remains **ROARR**.

ROARR adds a moment of visible character expression to an action the player already chooses to make. Pressing a watched action slot may lead to an in-game ROAR, CHARGE, CHEER, BORED or FLEX emote. The effect is deliberately light: a bit of mood, bravado, impatience or celebration rather than another combat mechanic.

The **act of playing** supplies the timing. ROARR does not scan the combat log or automate spell choices; it reacts to the player's button press. Two controls shape how present that response feels: the probability of a reaction and the minimum interval between opportunities. The addon can also be turned off without losing the setup.

## Relationship to earlier work

This origin is unusually clear in an early **2025-11-22 Lua source comment**: the first ROAR version was “Based on BuxbrewCharge, rewritten as ROAR with /roar slash command.” That is direct code evidence of an implementation lineage. The present ROARR is a **built-in-emote** addon, unlike Buxbrew's larger pool of bespoke written `EMOTE` sentences.

This does not prove a recovered conversation in which every design choice was individually proposed or accepted. Babuni is the project author; the assistance behind the first historical code and the reasons for each rename are not documented with a full dialogue.

## The ROAR guild connection

Looking back, I remember making this ROAR-themed experiment for the atmosphere of the **ROAR guild**. Yet its current source is an individual action-emote tool, without recruitment messages, guild membership checks, or invitation logic. The later **RoarGuild** addon contains the `/rogu invite` command for posting randomized recruitment text, not inviting a particular player through the game API.

## Creative boundaries

- Character presence, not ability automation or gameplay advantage.
- Five recognizable built-in WoW emotes, not a custom sound engine.
- Easy slot discovery through `/roarr watch`, no permanent UI clutter.
- Chance and cooldown make reactions intermittent; switch-off is deliberate and reversible.
- Chat commands and account-wide preferences keep it a small script.

The current source starts the cooldown **before** the chance roll. Consequently, a failed roll still delays the next opportunity. This behavioral detail is documented as implemented; whether that rhythm matches the creator's ideal is an open design question, not a newly approved change.

## Canonical identity boundaries

The GitHub repository was formerly `roar`; its installed addon remains `roarr`. The separate `babunidev/roarr` repository shares its gameplay code, differing in the tutorial. **RoarGuild** adds guild recruitment and community functionality, while **RoarForever** is another distinct addon. Shared naming does not prove a formal succession plan.

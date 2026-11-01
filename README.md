# Battle Emotes Legacy — battle emotes on an action slot

**By:** Babuni  
**Repository:** [`babunidev/BattleEmotesLegacy`](https://github.com/babunidev/BattleEmotesLegacy), formerly `roar`. **Installed addon:** `roarr`.  
**Target:** World of Warcraft 1.12 / interface `11200`  
**Declared version:** 1.0  
**Current runtime verification:** Not retested in this documentation review.

To distinguish this older experiment from the later Battle Emotes project, I renamed its GitHub repository **BattleEmotesLegacy**. The GitHub repository is now [`BattleEmotesLegacy`](https://github.com/babunidev/BattleEmotesLegacy), but its installed addon remains **ROARR**, with its original filenames and commands.

ROARR gives an ordinary action-bar press a little theatrical personality. After you choose a button, the addon can perform a randomly selected **built-in World of Warcraft emote**—ROAR, CHARGE, CHEER, BORED, or FLEX—without replacing that button's normal action. It's a lightweight character-flavor addon, not combat automation.

The original public description already emphasized chance and cooldown customization, an on/off switch, and a simple in-game tutorial. This expanded guide preserves that scope while documenting the current source behavior and development history.

## Installation

Place these files directly inside `Interface/AddOns/roarr/`:

```text
Interface/
  AddOns/
    roarr/
      roarr.toc
      roarr.lua
```

Restart the target WoW client and enable **ROARR**. The former repository name `roar` is historical; do **not** install a folder containing only the old `roar.lua` / `roar.toc` names from earlier Git commits.

## First setup

1. Type `/roarr watch` and press the action button that should trigger a reaction. The chat shows its slot number.
2. Set the slot, e.g. `/roarr slot 3`.
3. Turn watch-mode reports off by typing `/roarr watch` again.
4. Optionally choose `/roarr chance 40` and `/roarr cd 12`.
5. Use `/roarr on` or `/roarr off` without erasing the saved slot.

### Commands

| Command | Observed source behavior |
| --- | --- |
| `/roarr slot <number>` | Select and save watched action slot |
| `/roarr watch` | Toggle reports of pressed action slot IDs |
| `/roarr chance <0-100>` | Set percentage chance for a reaction after the cooldown gate |
| `/roarr cd <seconds>` | Set a nonnegative cooldown with no source-enforced upper limit |
| `/roarr on`, `/roarr off` | Enable or disable emote output; preserve saved settings |
| `/roarr info` | Show slot, chance, cooldown, enabled state, pool size |
| `/roarr reset` | Clear watched slot |
| `/roarr save` | Save settings to `ROARRDB` |
| `/roarr tutorial` | Print brief setup commands |
| `/roarr` | Print usage when no subcommand is supplied |

**Defaults:** enabled, 100% chance, **6-second** cooldown, no watched slot until configured. The current source uses one account-wide saved-variable table, `ROARRDB`.

## How the trigger really behaves

On pressing the configured slot, ROARR first checks that it is enabled and enough time has elapsed. **It sets the last-attempt time before rolling the random chance**. Thus a failed chance roll still consumes the cooldown; chance is not reevaluated on every press until the interval expires.

When the roll succeeds, ROARR chooses among five `DoEmote` tokens. The code falls back to a generic text emote if `DoEmote` is absent. The player's original action is then delegated to the previously captured `UseAction`. The addon does **not** verify that the underlying ability was cast successfully.

Other addons that hook global `UseAction` may interact with ROARR depending on load order. Client-specific emote behavior, localization, and actual compatibility require live testing.

## How it differs from the other action-emote addons

| Project | Emote content | Default cooldown | Adjustable chance / cooldown | Guild recruitment |
| --- | --- | --- | --- | --- |
| [Action Emotes #1](https://github.com/babunidev/ActionEmotes-1), originally BuxbrewCharge | 10 built-in emotes | 21 seconds | No / No | No |
| [Action Emotes #2](https://github.com/babunidev/ActionEmotes-2), originally Buxbrew | 215 custom written emotes | 90 seconds | No / No | No |
| **Battle Emotes Legacy** (this project) | **5 built-in battle emotes** | **6 seconds** | **Yes / Yes** | **No** |
| [`roarr`](https://github.com/babunidev/BattleEmotes), separate project | Same five built-in battle emotes | 6 seconds | Yes / Yes | No |

The current Lua files of the two ROARR repositories have **identical gameplay code**. Their observed difference is the help presentation: Battle Emotes Legacy has a condensed `/roarr tutorial`; the separate `roarr` repository has a seven-step tutorial. Git does not establish why both repositories were originally maintained.

Looking back, I associate this experiment with the **ROAR guild**. That connection is part of the project's history, but **guild invitation and recruitment features are absent from both ROARR versions**. The later [RoarGuild](https://github.com/babunidev/RoarGuildAddon) addon contains the remembered `/rogu invite` command, which posts a random recruitment message to a numbered chat channel on request. It does not send a game invitation to a player.

## Project history and naming

The first source upload on **2025-11-22** called this addon **ROAR**, explicitly describing it in a source comment as *based on BuxbrewCharge*. Development on **2025-11-23** added and adjusted configuration, on/off handling, and changed names between `roar` and `roarr` several times. The final committed package is **ROARR**, using `/roarr` and `ROARRDB`.

The separate `roarr` repository has the same core implementation, whereas RoarGuild and the later **RoarForever** have different features. No code dependency on those projects appears in this source.

## License and attribution

**Creative/project author:** Babuni. The repository includes an **MIT `LICENSE` file** with the historical copyright line `Copyright (c) 2025 Elexior`. That wording has been left untouched. The relationship between the historical copyright holder and the current display author has not been independently established in this review; confirm attribution before changing legal language. The casual permission wording in the former README is not a substitute for the committed MIT license.

## Documentation

- [Creative concept](CONCEPT.md) · [Interaction design](docs/DESIGN.md) · [Emote content](docs/CONTENT.md)
- [Technical architecture](docs/ARCHITECTURE.md) · [Decisions and alternatives](docs/DECISIONS.md) · [Development journal](docs/DEVLOG.md)
- [Roadmap / verification](ROADMAP.md) · [Changelog](CHANGELOG.md)
- [Human–AI collaboration](docs/AI_COLLABORATION.md) · [Developer instructions](AGENTS.md)

This project record distinguishes the human creative's authorship, AI documentation assistance, historically observable code changes, and behavior that has not yet been checked in-game.

## Place in the larger emote history

Battle Emotes Legacy is the November 2025 ROAR experiment derived from BuxbrewCharge. Its five battle-emote tokens (ROAR, CHARGE, CHEER, BORED and FLEX) are a **fixed Lua table**, not a starting set the player can extend with commands. It adds adjustable chance/cooldown and an on/off switch, but not guild recruitment. The separate Battle Emotes repository has effectively the same gameplay implementation and a longer tutorial. The [cross-repository history](docs/EMOTE_FAMILY_HISTORY.md) explains where editable emote pools actually appeared: later in Roar Guild Addon and its Wrath port.

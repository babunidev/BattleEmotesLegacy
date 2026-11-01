# Battle Emotes Legacy — interaction and presentation design

The project is now named **Battle Emotes Legacy** on GitHub; the addon itself retains the historical **ROARR** identity. In this record, I keep these names distinct from the separate `roarr` repository.

**By:** Babuni

## The little surprise

ROARR is designed around a player action rather than a scheduled spectacle. A familiar combat button can suddenly be accompanied by a roar, flex, cheer or playfully bored response. This lets the player retain direct control of combat while the character acquires an occasional independent-looking expressive moment.

The response uses **WoW built-in emotes**. No custom avatar animation, dedicated audio asset, widget, or complex command window is shipped.

## Frequency and probability

Two controls change the cadence:

- **Chance** governs whether an eligible emote attempt succeeds (`/roarr chance 0..100`).
- **Cooldown** governs how often eligible attempts can happen (`/roarr cd <seconds>`), starting at six seconds.

A failed chance roll **still consumes the cooldown** in source. This means `chance 40; cd 12` is not “a 40% roll on every press”: a failed attempt delays the next eligible roll by twelve seconds. Whether that is the desired game feel is left open to the creator.

An on/off switch lets the player silence reactions without losing slot or chance preferences. The watch switch prints slot IDs and is meant as a temporary configuration aid, not a permanent player overlay.

## Output vocabulary and social tone

| Token | Expressive role |
| --- | --- |
| `ROAR` | Battle excitement and loud assertion |
| `CHARGE` | Momentum and aggressive enthusiasm |
| `CHEER` | Celebration and encouragement |
| `BORED` | Comic contrast with the fight |
| `FLEX` | Pride and swagger |

The variety is small but effective: even `BORED` contributes personality by interrupting battle intensity with an incongruous emotion. Which of the five tokens is chosen is random and unweighted.

## User journey

Enter `/roarr watch`, discover the slot, set it, optionally adjust chance and cooldown, turn off watch mode and play normally. `/roarr tutorial` offers a short reminder; `/roarr info` reports the live configuration. All feedback appears in the chat frame, prefixed `ROARR:`.

## Accessibility and client-specific unknowns

Text setup can be challenging if slot numbering changes between bar layouts; the discovery switch helps. Test whether the five emotes make sense in the player's client/locale and whether spam prevention and UI messages remain comfortable. There is no evidence of accessibility testing or broad client validation in the repository.

## Naming

The GitHub repository is **BattleEmotesLegacy**, formerly `roar`; the installed addon remains **ROARR**. The separate `roarr` repository has a longer tutorial but the same gameplay code. Babuni associates this experiment with the ROAR guild, while the actual guild-recruitment messages belong to the later RoarGuild addon.

## Place in the expressive-addon family

Battle Emotes Legacy is the November 2025 ROAR experiment derived from BuxbrewCharge. Its five battle-emote tokens (ROAR, CHARGE, CHEER, BORED and FLEX) are a **fixed Lua table**, not a starting set the player can extend with commands. It adds adjustable chance/cooldown and an on/off switch, but not guild recruitment. The separate Battle Emotes repository has effectively the same gameplay implementation and a longer tutorial. See [the source-grounded family timeline](EMOTE_FAMILY_HISTORY.md) for the differences between all the projects.

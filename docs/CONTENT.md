# Battle Emotes Legacy — emote and UI text inventory

**Author:** Babuni  
**Canonical source:** `EMOTE_TOKENS_BATTLE` in `roarr.lua`.

## Built-in emote tokens

| Token in source | Familiar slash-emote concept | Narrative purpose |
| --- | --- | --- |
| `ROAR` | roar | Battle cry |
| `CHARGE` | charge | Momentum |
| `CHEER` | cheer | Celebration |
| `BORED` | bored | Comic contrast |
| `FLEX` | flex | Strength/swagger |

ROARR passes a randomly chosen token to `DoEmote`. The text/animation experienced by nearby players is supplied by the **game client**, not by an embedded custom audio or animation file. Token availability on a specific client has not been verified in this documentation pass.

If `DoEmote` is absent, the Lua fallback posts the short generic string “makes a battle cry!” in `EMOTE` chat.

## Other player-facing writing

- Slash command prefix: `/roarr`, with `ROARR:` message label.
- Setup/status commands: `slot`, `watch`, `chance`, `cd`, `on`, `off`, `info`, `reset`, `save`, `tutorial`.
- Tutorial: a compact series of configuration commands, not a graphical wizard.
- Invalid command: concise usage text; invalid chance/cooldown produces its corresponding usage guidance.

## Where the guild messages live

The **ROAR guild** is part of Babuni's recollection of this project, but the current Lua contains **no invitation or recruitment text**. The separate `roarr` repository uses the same five built-in emotes with a more detailed tutorial. The later [RoarGuild](https://github.com/babunidev/RoarGuild) addon contains the manually triggered randomized recruitment messages.

## Editorial maintenance

Do not replace the five built-in tokens with bespoke text strings without Babuni's direction. Content changes should distinguish gameplay effects, specific game-owned emotes and Babuni's own addon-authored strings.

Historical source variants used `ROAR`, `/roar` and `ROARDB`; the final package uses the distinct `ROARR` namespace. See `docs/DEVLOG.md` for source-backed evolution.

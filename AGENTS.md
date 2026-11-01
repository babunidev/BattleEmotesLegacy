# Battle Emotes Legacy — development collaboration rules

**By:** Babuni.

## Documentation voice and naming

Write the public project history from Babuni's first-person perspective. Never begin a narrative sentence with “I” or “My”; weave first-person language naturally. Refer to the person as **Babuni** and to **babuni.dev** only as the wider development portfolio. Attribute AI's code, research and documentation to the assistant actually directed, without inventing original conversations or approvals. Use **creative**, not **creator**, for the human role label. Neutral technical prose is acceptable.

The GitHub repository is **BattleEmotesLegacy**, displayed as **Battle Emotes Legacy**. The installed addon uses `roarr.lua`, `roarr.toc`, `/roarr` and `ROARRDB`. Do not silently rename those identifiers. Document that the separate `roarr` repo shares the gameplay implementation but offers a longer tutorial. Do not confuse this code with RoarGuild's recruitment system or RoarForever.

## Protect the work's identity

The current repository is `babunidev/BattleEmotesLegacy`. The installed addon is **ROARR** with files `roarr.lua` and `roarr.toc`, slash command `/roarr` and DB `ROARRDB`. A **different** GitHub repository named `roarr` and the separate **RoarForever** project must not be silently merged into this history.

The core experience is player-triggered battle emotes, with configurable chance, cooldown and enable state. Do not convert it into combat automation or a different visual system without explicit direction from Babuni.

## Standards

1. Before changing anything, inspect `README.md`, `CONCEPT.md`, `docs/DEVLOG.md`, `docs/DECISIONS.md`, `roarr.lua` and `roarr.toc`.
2. Record **creative direction**, **AI proposals**, **accepted/rejected alternatives**, **actual changes**, **commit references** and **verification evidence** separately.
3. Use dated Git diffs for historical claims. Do not invent reasons for repeated November 2025 renames, deletions or code revisions.
4. Maintain Babuni credit, but **preserve the existing MIT license** and its historical 2025 copyright line until appropriate ownership clarification; never rewrite legal attribution speculatively.
5. Treat the code as evidence of implementation, not as proof of live WoW compatibility. List untested edge cases.
6. For future changes, keep README, CHANGELOG, ARCHITECTURE, DEVLOG, DECISIONS, DESIGN and CONTENT consistent with code.
7. Avoid private chat archives, player names, credentials and unapproved historical excerpts in public docs.

## Implementation checks

- Stay compatible with World of Warcraft 1.12 and Lua 5.0 unless Babuni changes the requirement.
- Review global `UseAction` hook chaining with other addons.
- Preserve saved preferences in `ROARRDB`; check initialization and logout behavior.
- Know that a failed chance roll currently still starts the cooldown.
- Verify rather than assume all built-in emote tokens exist on the user's client.
- Run and report actual tests before marking gameplay verified.

## Verified family distinction

Battle Emotes Legacy and the separate `roarr` project have the same five-token emote mechanics; their tutorial output differs. The guild association is Babuni's recollection, but **neither source includes guild recruitment**. That appears in the later **RoarGuild** project as manual chat messages. Do not infer automatic guild joining, integration, or an approved merger.

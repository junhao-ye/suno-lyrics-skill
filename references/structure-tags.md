# Structure Tags

Open this when choosing Suno lyric section tags, performance notes, ad-libs, or punctuation controls.

## Core Song Structure

| Use case | Structure |
|----------|-----------|
| Standard pop | `[Intro] [Verse 1] [Pre-Chorus] [Chorus] [Verse 2] [Pre-Chorus] [Chorus] [Bridge] [Final Chorus] [Outro]` |
| Short catchy song | `[Intro] [Verse] [Chorus] [Verse 2] [Chorus] [Outro]` |
| Rap | `[Intro] [Rap Verse 1] [Hook] [Rap Verse 2] [Hook] [Bridge] [Final Hook]` |
| EDM | `[Intro] [Verse] [Build-Up] [Drop] [Verse 2] [Build-Up] [Final Drop] [Outro]` |
| Ballad | `[Intro: Piano] [Verse 1] [Pre-Chorus] [Chorus] [Verse 2] [Bridge] [Final Chorus] [Outro]` |
| Instrumental sections | `[Instrumental] [Piano Solo] [Guitar Solo] [Breakdown] [Interlude]` |
| Continuation / Extend | `[Verse 2] [Bridge] [Final Chorus] [Outro]` or the next logical section only |

## Tag Types

| Tag | Use |
|-----|-----|
| `[Intro]` | Sets mood before vocals. |
| `[Verse]` | Story, image, situation, or argument. |
| `[Pre-Chorus]` | Lift into the hook. |
| `[Chorus]` | Main hook and repeatable emotional center. |
| `[Post-Chorus]` | Short chant or melodic payoff after chorus. |
| `[Bridge]` | Contrast, twist, new perspective. |
| `[Hook]` | The most memorable repeated phrase. |
| `[Outro]` | Closure, fade, or final image. |
| `[Rap Verse]` | Dense rhythm and internal rhyme. |
| `[Build-Up]` / `[Drop]` | EDM tension and release. |

## Performance Notes

Use performance notes sparingly. Over-tagging can make Suno ignore the most important instructions.

| Note | Example |
|------|---------|
| Vocal | `[Female Vocal]`, `[Male Vocal]`, `[Duet]`, `[Falsetto Chorus]` |
| Mood | `[Verse: Calm]`, `[Chorus: Anthemic]`, `[Bridge: Intimate]` |
| Arrangement | `[Piano Intro]`, `[No Drum Chorus]`, `[String Bridge]` |
| Texture | `[Whispered]`, `[Layered Vocals]`, `[Harmony Stack]` |
| Energy | `[Build-Up]`, `[Half-Time]`, `[Power Chorus]` |

## Parentheses And Ad-Libs

Use parentheses for backing vocals, callouts, and texture:

```text
(ooh)
(yeah)
(hold on)
(call and response)
```

Keep them short. Too many ad-libs can disrupt phrasing.

## Punctuation And Line Breaks

| Choice | Effect |
|--------|--------|
| Short lines | Clearer phrasing and stronger rhythm. |
| Four-line sections | Usually easiest for Suno to interpret. |
| Commas | Gentle phrase grouping. |
| Exclamation marks | Higher energy or emphasis. |
| Questions | Can add melodic lift or pause. |
| Ellipses | Use cautiously; may feel like an ending. |
| All caps | Use only for a single emphasized word or chant. |

## Structure Checks

- Avoid more than two bracketed descriptors on one line.
- Number verses only when it improves clarity.
- Repeat the chorus with small variation for payoff.
- For continuation/extend workflows, repeat the previous section's last line only when continuity matters.
- For instrumental prompts, use section tags only if the user wants arrangement control; otherwise keep control in `Style of Music`.

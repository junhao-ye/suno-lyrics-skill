# Style Prompts

Open this when building `Style of Music`, `Exclude Styles`, instrumental prompts, vocal traits, or genre recipes.

## Style Formula

Use this order when the user gives enough detail:

```text
genre/subgenre, mood, tempo or BPM, instrumentation, vocal type, production texture, era/reference traits
```

Example:

```text
Mandarin acoustic pop ballad, warm and melancholic, 76 BPM, fingerpicked guitar, soft piano, female vocal, intimate studio production
```

If the lyrics are not English, name the language near the start of the style prompt.

## Style Components

| Component | Examples |
|-----------|----------|
| Genre | pop, R&B, hip-hop, rock, folk, EDM, synthwave, jazz, country |
| Mood | melancholic, uplifting, romantic, eerie, cinematic, playful |
| Tempo | slow 70 BPM, mid-tempo 96 BPM, upbeat 124 BPM |
| Instruments | piano, acoustic guitar, strings, 808 bass, synth pads, live drums |
| Vocal | female vocal, male vocal, duet, rap, spoken word, choir, falsetto |
| Texture | lo-fi, glossy, spacious, intimate, distorted, orchestral, dry vocal |
| Era | 80s synth pop, 90s R&B, 2000s pop rock, modern trap |

## Voice And Persona Handling

| Situation | Do |
|-----------|----|
| User asks for a voice type | Use traits such as `soft female vocal`, `warm baritone`, `clear lead vocal`. |
| User names a living artist | Convert to neutral traits: era, genre, instruments, tempo, vocal energy, mix texture. |
| User has Suno Voice/Persona/Custom Model | Mention they can select it in Suno; do not invent a specific voice field. |
| User wants to change an existing voice | Prefer Reuse Prompt or Studio guidance; style text alone may not alter the rendered audio. |

## BPM Guide

| BPM | Fit |
|-----|-----|
| 60-80 | ballad, folk, sad pop, worship |
| 80-100 | R&B, hip-hop, relaxed pop |
| 100-120 | pop, rock, danceable mid-tempo |
| 120-130 | EDM, house, energetic pop |
| 130+ | drum and bass, speed, high-energy electronic |

## Exclude Styles

Use comma-separated items. Put the things the user does not want here rather than writing "no..." in the main style prompt.

Good exclude examples:

```text
metal, hard rock, screaming vocals, distorted guitar, live crowd noise
```

```text
vocals, singing, choir, chanting, spoken word, humming
```

For instrumental requests, remove vocal-positive words from `Style of Music`, then exclude all vocal forms that might appear.

## Common Style Recipes

| Goal | Style of Music |
|------|----------------|
| Mandarin heartbreak ballad | Mandarin pop ballad, melancholic, 72 BPM, piano, strings, female vocal, emotional chorus |
| Urban night R&B | late-night R&B, 86 BPM, warm Rhodes, sub bass, brushed drums, smooth male vocal |
| Energetic brand anthem | upbeat pop rock, 120 BPM, bright guitars, punchy drums, group chorus, uplifting |
| Cyberpunk | dark synthwave, 105 BPM, analog synth bass, gated drums, atmospheric pads, cool female vocal |
| Rap motivation | boom bap hip-hop, 92 BPM, hard drums, bass groove, confident rap vocal, minimal hook |
| Folk warmth | acoustic folk pop, 78 BPM, fingerpicked guitar, light percussion, intimate vocal, organic |
| Instrumental cinematic | cinematic instrumental, 82 BPM, felt piano, low strings, soft percussion, spacious emotional production |
| Instrumental electronic loop | instrumental ambient electronic, 96 BPM, analog synth pads, pulsing bass, subtle percussion, evolving lead synth |

## Prompt Hygiene

- Keep style prompts specific but not overloaded.
- Avoid contradictory pairs such as "minimal orchestral EDM metal acoustic ballad."
- Put the most important sound first.
- Mention a named artist only if the user provided it for context, then convert it into traits in the output.
- Use `Exclude Styles` for unwanted sounds instead of negative wording in `Style of Music`.
- Do not put the same concept as desired and excluded.
- Avoid account/UI-only controls in the style field; keep them as a short note when relevant.

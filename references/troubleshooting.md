# Troubleshooting

Open this when fixing bad Suno outputs or improving a prompt after listening.

## Diagnosis Matrix

| Symptom | Likely cause | Fix |
|---------|--------------|-----|
| Wrong genre | Style prompt too vague or conflicting | Rewrite style with one primary genre first. |
| Chorus is weak | Hook not repeated or not distinct | Add a shorter chorus with a repeated title phrase. |
| Lyrics sound generic | Abstract wording and AI cliches | Replace with concrete images and specific actions. |
| Vocals appear in instrumental | Vocal-related words in style or lyrics box | Remove voice terms; add `vocals, singing, choir, spoken word` to excludes. |
| Exclude ignored | Main prompt still implies excluded sound | Remove contradictory desired traits and restate desired sound positively. |
| Voice is wrong | Vocal traits too vague, existing audio cannot be directly changed, or no Suno Voice/Persona selected | Use clearer vocal traits for a new generation; use Reuse Prompt or Studio for existing songs. |
| Lyrics or voice need editing after generation | Suno rendered one combined audio file | Use Reuse Prompt to make a new version; use Studio/stems only for deeper editing. |
| Song feels too slow | No tempo/energy cue | Add BPM and rhythm words such as upbeat, driving, danceable. |
| Song feels too busy | Too many tags or genres | Reduce to one genre, one mood, three instruments. |
| Rap lacks flow | Lines too long or end rhymes absent | Shorten bars and add internal rhyme. |
| Language is mixed unexpectedly | Style prompt implies foreign genre/vocal | State the target language in lyrics and style. |
| Ending cuts off | Too much lyric content | Shorten sections or add `[Outro]` with final line. |
| Repeated retries do not improve | Too many variables changed at once | Change lyrics, style, or excludes one at a time and compare. |

## Iteration Rules

1. Change one variable per retry when diagnosing.
2. Keep a good chorus intact if only the style is wrong.
3. Keep a good style prompt intact if only the lyrics are weak.
4. Use Reuse Prompt for near-miss generations.
5. If the model keeps ignoring a negative instruction, remove the conflicting positive cue and describe the desired alternative.
6. For instrumental failures, delete all lyric text and vocal descriptors before adding vocal excludes.

## Fast Fix Patterns

### More emotional

```text
Add: intimate vocal, sparse first verse, emotional chorus, piano and strings
```

### More energetic

```text
Add: 124 BPM, driving drums, power chorus, bright synths, group chant
```

### Cleaner vocal

```text
Add: clear lead vocal, dry vocal mix, minimal backing vocals
Exclude: heavy reverb, crowd noise, distorted vocals
```

### Fix instrumental vocals

```text
Style: cinematic instrumental, 78 BPM, felt piano, cello, soft percussion, spacious film-score production
Exclude: vocals, singing, choir, chanting, spoken word, humming, rap
Note: enable Instrumental in Suno.
```

### Less generic

```text
Replace abstract lines with place, object, action, and consequence.
```

## Do Not

- Do not add every possible tag to force control.
- Do not put the same unwanted word in both style and exclude fields.
- Do not keep regenerating without changing either lyrics, style, or exclude prompt.
- Do not promise that a text prompt can surgically edit one rendered vocal line; create a new version or use Studio features.

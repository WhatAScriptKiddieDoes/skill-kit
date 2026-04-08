---
name: generate-artist
disable-model-invocation: true
description: Generate a detailed AI artist profile document for use in Google Lyria song generation and lyrics writing. Invoke when the user wants to create or define a new music artist persona.
argument-hint: <artist concept, genre, mood, or any starting idea>
---

# PURPOSE

Generate a comprehensive artist profile document for an AI-generated music channel. The output serves two downstream systems:

1. **Lyrics generation** — needs voice, themes, vocabulary, emotional tone, storytelling style
2. **Google Lyria song generation** — needs precise musical descriptors: genre tags, instrumentation, tempo, mood, production style, vocal style

The profile must be detailed enough that either system can produce consistent, on-brand output without additional context.

---

# STEPS

1. Read the user's input and infer or extrapolate: genre, mood, era influences, audience, voice type, production style
2. Assign the artist a name if the user hasn't provided one (make it feel authentic to the genre)
3. Generate each section below with rich, specific detail — avoid vague descriptors like "unique" or "interesting"
4. For every musical attribute, include the kind of language Google Lyria expects (tempo BPM ranges, key/mode, instrument list, production tags)
5. For lyric-relevant sections, include vocabulary level, common themes, narrative POV, and emotional arc patterns
6. End with a "Lyria Prompt Seed" block — a ready-to-use base prompt string for Google Lyria

---

# OUTPUT INSTRUCTIONS

- Output a single Markdown document
- Use `##` for section headers, `###` for subsections
- Keep each section self-contained so it can be copy-pasted independently
- Be specific and concrete — "melancholic fingerpicked acoustic guitar, DADGAD tuning" beats "acoustic sound"
- Do not add caveats, disclaimers, or meta-commentary — output only the artist document
- End with a horizontal rule and a `## Lyria Prompt Seed` block containing a ready-to-paste prompt string

---

# OUTPUT FORMAT

The document must contain these sections in order:

```
# [ARTIST NAME]
> [One-sentence artist logline]

## 1. Artist Concept & Identity
## 2. Genre & Subgenre
## 3. Musical Style & Sound
   ### Instrumentation
   ### Production Style
   ### Tempo & Structure
   ### Key / Mode / Harmony
## 4. Vocal Profile
   ### Voice Type & Range
   ### Delivery & Technique
   ### Backing Vocals & Harmonies
## 5. Lyrical Identity
   ### Core Themes
   ### Narrative POV & Storytelling Style
   ### Vocabulary & Language Register
   ### Emotional Arc Patterns
   ### Sample Lyric Imagery (3–5 lines of example)
## 6. Target Audience
   ### Demographics
   ### Psychographics
   ### Platform & Discovery Context
## 7. Influences & Reference Artists
## 8. Song Structures (typical patterns)
## 9. Visual & Brand Identity (for YouTube channel use)
## 10. Dos and Don'ts
    ### Always
    ### Never
## 11. Lyria Prompt Seed
```

---

# INPUT

$ARGUMENTS

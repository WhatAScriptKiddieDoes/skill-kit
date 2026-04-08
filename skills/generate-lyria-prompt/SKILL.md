---
name: generate-lyria-prompt
disable-model-invocation: true
description: Generate a complete, paste-ready Gemini Lyria 3 song generation prompt from an artist description file and a set of lyrics. Adapts the sound description to the specific song's content, structure, and emotional arc. Invoke after lyrics have been written for an artist.
argument-hint: <@ArtistFile.md> <@lyrics-or-paste-lyrics> [optional: any specific production notes]
---

# PURPOSE

Produce a single, complete prompt block that can be pasted directly into Gemini Lyria 3 to generate a song. The prompt must be specific enough that Lyria can produce a result consistent with the artist's sound profile AND the unique character of this specific song — not a generic genre description.

The output is a production document, not a creative exercise. Every element must be actionable by a music generation model.

---

# PROCESS

## Step 1 — Extract Artist Sound DNA

From the artist file, extract and hold:

- **Instrumentation list:** Every instrument, with playing style and role (e.g. "drop-B palm-muted electric guitar, verse only; power chord walls on chorus")
- **Production tags:** The exact mixing and production descriptors from the profile
- **Tempo and BPM range**
- **Key, mode, and harmonic movement patterns**
- **Vocal profile:** Voice types, delivery style, range, technique rules, what is explicitly excluded
- **Energy curve:** How the track moves from intro to final chorus
- **Reference artists/tracks** listed in the profile — use these as Lyria-facing anchors
- **The Lyria Prompt Seed** from the profile — use it as the base, not as the final prompt

## Step 2 — Read the Lyrics

Analyze the lyrics for:

- **Emotional arc:** What is the emotional journey from verse 1 to final chorus? Where is the peak? Is there a moment of doubt in the bridge?
- **Thematic core:** What is this specific song actually about? What is its central image or argument?
- **Pacing and density:** Are the verses dense and fast-cadence, or sparse and deliberate? Does the chorus open up or compress?
- **Section-specific tone:** Does the bridge strip back or intensify? Does the outro cut or fade?
- **Key lyric moments:** Identify 2–3 lines that are the emotional or sonic peak of the song — these will anchor the production notes

## Step 3 — Adapt the Sound Description to the Song

This step is the core of the skill. A generic artist prompt is not the goal — a prompt tuned to THIS song is.

Apply the following adaptations:

- **Tempo:** If the lyrics are dense and rap-cadence, lean to the upper BPM range. If the verse is spare and declarative, lean to the lower end. State the BPM explicitly.
- **Arrangement dynamics:** Describe the specific dynamic shape of THIS song based on the lyrics' arc, not just the artist's standard curve. If the bridge strips to near-silence, say so. If the final chorus stacks three vocal layers, say so.
- **Vocal casting per section:** Map each vocal style to each section using the actual section names from the lyrics (e.g. "Verse 1: male baritone spoken-word, declarative cadence; Chorus: female mezzo-soprano power-belt hook + male bark doubles").
- **Thematic color in the production:** If the song is about endurance under pressure, note that strings should feel relentless and unresolved through the verses. If the song is about a single decisive moment, note the arrangement should hold tension until the chorus detonation.
- **Instrument emphasis by section:** Specify which instruments lead in which sections based on the song's arc (e.g. "Verse 1 driven by cello ostinato and kick only; pre-chorus adds guitar chug; chorus: full ensemble explosion").

## Step 4 — Write Per-Section Production Notes

For the 3–5 most important structural sections of the song (typically: verse 1 setup, pre-chorus build, chorus peak, bridge, final chorus), write a 1–2 sentence production note that Lyria can use as a section-level instruction. These are appended at the end of the main prompt.

Example format:
> **[VERSE 1]:** Sparse — cello ostinato, kick drum, no guitar. Male voice close and dry, no reverb. The arrangement holds back completely.
> **[CHORUS]:** Full detonation. All instruments enter simultaneously. Female vocal belt on the hook. Male bark doubles key words an octave below. Choir stabs on downbeats.

## Step 5 — Minor Lyric Adaptation (if needed)

If a word or phrase in the lyrics would be ambiguous, unsingable, or poorly suited to the arrangement as described (e.g. a line that's too long for the tempo, a word that clashes with the cadence pattern), make the minimal edit required. Do not change meaning, imagery, or any line that works. Flag any changes made at the end of the output in a single parenthetical note.

## Step 6 — Assemble the Final Prompt

Structure the output as a single block with clearly labeled sections. The full prompt must be self-contained: someone pasting it into Lyria should need nothing else.

---

# OUTPUT FORMAT

```
=== LYRIA 3 GENERATION PROMPT ===

## ARTIST
[Full artist identity paragraph — pulled directly from the artist file's concept & identity section, written as a dense production brief. Do not invent new attributes; do not omit key ones. This section describes WHO is performing this song.]

## SOUND PROFILE
[Complete instrumentation list with roles and playing styles. Production tags. Mixing approach. What is explicitly excluded. Reference artists and tracks. This section describes HOW the song sounds at a technical level.]

## THIS SONG
[Title, BPM, key, mode. Thematic core in 1–2 sentences. Emotional arc of the song. The 2–3 lyric lines that represent the sonic and emotional peak.]

## ARRANGEMENT MAP
[Section-by-section instrument/dynamic description, customized to THIS song's arc. Written as a compact list, one entry per section.]

## VOCAL CASTING
[Explicit assignment of vocal style to each section. Male verse delivery style. Female chorus delivery style. Any choir, doubles, or bark overlays, and where they appear.]

## FULL LYRICS
[The complete lyrics, formatted with section labels, exactly as provided — with any minor adaptations applied if Step 5 produced changes.]

## SECTION PRODUCTION NOTES
[Per-section production guidance for the 3–5 most important moments. Each note is 1–2 sentences.]
```

Rules:
- Output the prompt block only — no preamble, no explanation before the `=== LYRIA 3 GENERATION PROMPT ===` line
- If minor lyric edits were made in Step 5, add a single line after the block: `(Lyric adaptations: [brief description of what was changed and why])`
- Do not add any other commentary after the prompt block
- The prompt must be usable as a direct paste — no placeholders, no incomplete fields

---

# INPUT

$ARGUMENTS

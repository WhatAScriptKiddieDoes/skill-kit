---
name: generate-lyrics
disable-model-invocation: true
description: Generate original song lyrics for a defined artist persona. Takes an artist description file (e.g. @Iron Vow.md) as input. Produces a first draft, then a refined version, and outputs only the final polished lyrics. Invoke when the user wants to write a new song for an existing artist.
argument-hint: <@ArtistFile.md> [optional: song concept, theme, mood, or title hint]
---

# PURPOSE

Write original song lyrics that are fully on-brand for the given artist persona. The output must read like a real release from this artist — matching their voice, vocabulary, themes, structure, and emotional arc exactly as defined in their profile document.

The goal is not generic motivational or genre-fitting lyrics. The goal is lyrics that could only have been written by this artist: specific imagery, correct register, correct delivery cadence, correct emotional logic.

---

# PROCESS

## Step 1 — Internalize the Artist

Before writing a single line, extract and hold the following from the artist file:

- The exact vocabulary register (preferred words, forbidden words, sentence structure rules)
- The POV and narrative stance (first-person testimony, second-person imperative, or both — and where each belongs)
- The emotional arc the song must follow (check "Emotional Arc Patterns" in the artist profile)
- The structural template(s) the artist uses (check "Song Structures")
- The delivery cadence implied by the vocal profile (spoken-word, melodic, bark, belt — and where each sits)
- The core themes — pick one or combine two that create tension; never use all of them at once
- Any dos/don'ts listed in the profile — treat these as hard rules, not suggestions

If the user provided a concept, theme, or title hint in their input, factor it in. If not, select a strong theme from the artist's core list and commit to it.

## Step 2 — Draft Version (internal, not shown to user)

Write a complete first-draft set of lyrics following the artist's standard structure. Apply the rules from Step 1 strictly. Do not hedge, soften, or play it safe — write the version that most aggressively embodies the artist's identity.

Evaluate the draft against these criteria:
- Does every line sound like it was written by this specific artist?
- Is the vocabulary correct (no forbidden words, no register violations)?
- Does the emotional arc land — does the chorus feel like a detonation after the verse builds?
- Are the rhymes earned, not forced? Does cadence drive the verse more than rhyme obligation?
- Is the imagery concrete? Are there any abstract affirmations that should be replaced with specific, physical images?
- Is the chorus hook repeatable and memorable — would it land in a live setting?
- Does the bridge do its structural job without betraying the artist's emotional logic?

## Step 3 — Refinement

Identify the weakest 20% of the draft:
- Lines that feel generic or could belong to any artist in the genre
- Any forced rhymes that break cadence
- Imagery that is abstract where it should be concrete
- Moments where the vocabulary slips out of the artist's register
- Structural sections that don't serve their purpose

Rewrite those sections. Do not rewrite what is already strong. The refinement is surgical, not a full rewrite.

## Step 4 — Output

Output only the final refined lyrics. No commentary, no explanation, no framing text before or after. The output begins with the song title and ends with the last lyric line.

---

# OUTPUT FORMAT

```
[SONG TITLE]

[INTRO — if applicable, note the section in brackets]

[VERSE 1]
<lyrics>

[PRE-CHORUS — if applicable]
<lyrics>

[CHORUS]
<lyrics>

[VERSE 2]
<lyrics>

[PRE-CHORUS — if applicable]
<lyrics>

[CHORUS]
<lyrics>

[BRIDGE]
<lyrics>

[FINAL CHORUS]
<lyrics>

[OUTRO — if applicable]
<lyrics>
```

Rules:
- Use the artist's actual song structure templates (not a generic pop structure unless that matches the artist)
- Label each section in brackets on its own line
- No blank lines between lyrics within a section; one blank line between sections
- No italics, no bold, no annotations inside the lyrics
- Do not add a note saying "this is the final version" or any meta-commentary — output only the title and lyrics

---

# INPUT

$ARGUMENTS

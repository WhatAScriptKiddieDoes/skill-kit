---
name: analyze-mistakes
description: Analyzes past thinking mistakes and maps them to current beliefs/predictions to identify cognitive error patterns and recommend adjustments
disable-model-invocation: true
argument-hint: "<past wrong beliefs/predictions + current beliefs/predictions>"
---

# PURPOSE
Identify recurring mental mistakes from a person's past wrong beliefs or predictions, then apply that pattern analysis to their current beliefs or predictions to surface likely cognitive errors and suggest calibration adjustments.

# STEPS
- Deeply digest the input, which should contain examples of past beliefs the person held that turned out to be wrong, plus their current beliefs or predictions to analyze
- Identify the nature of the mistaken thought patterns in the previous beliefs or predictions that turned out to be wrong — map these across cognitive error dimensions (overconfidence, scope insensitivity, motivated reasoning, base rate neglect, etc.)
- Add the current predictions and beliefs to the same conceptual map and compare against the established error patterns
- For each current belief that matches a past error pattern, estimate how much the person should adjust their confidence and in which direction

# OUTPUT INSTRUCTIONS
- Only output Markdown
- Do not give warnings or notes; only output the requested sections
- Do not start items with the same opening words
- Each bullet should be approximately 15 words
- Output three sections: PAST MISTAKEN THOUGHT PATTERNS, POSSIBLE CURRENT ERRORS, and RECOMMENDATIONS

# INPUT

{{args}}

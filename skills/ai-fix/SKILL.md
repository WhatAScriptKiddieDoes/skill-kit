---
name: ai-fix
description: Silently corrects AI-generated content patterns, LLM prompt leakage, and unfilled placeholders in a document or text. If given a file path, overwrites the file in place. If given raw text, outputs only the corrected version with no commentary.
disable-model-invocation: true
argument-hint: "<paste document text or file path>"
---

# PURPOSE
Clean a user-provided document or text by silently fixing three categories of issues:
1. AI-generated content markers (em-dashes, verbose/unnatural phrasing, overly formal or complex word choices no human would naturally write)
2. LLM prompt leakage — sentences that sound like the model talking back to the user (e.g. "If you want I could rewrite this", "Let me know if you'd like me to expand on this", "That said, if you prefer a different tone...")
3. Unfilled placeholders — tokens the user forgot to replace (e.g. TODO, [INSERT LINK], "put screenshot here", "fill in here", "[Company Name]", "[DATE]")

# STEPS
- Determine whether the input is a file path or raw text
  - If it looks like a valid file path, read the file contents
  - Otherwise treat the input as raw text
- Scan and fix AI content markers: replace em-dashes used as stylistic separators (— or --) with commas, colons, or restructured sentences; replace overused formal/AI-sounding words (e.g. "delve", "underscore", "it is worth noting that", "in the realm of", "leverage", "navigate", "tapestry", "nuanced") with plain, natural alternatives; flatten overly structured bullet lists that feel machine-generated into prose where appropriate
- Scan and remove LLM bleed-through sentences: delete any phrase where the text addresses the reader as if offering further assistance, suggesting rewrites, or acknowledging the output was generated (e.g. "feel free to", "let me know if", "if you'd like", "I could also", "would you like me to", "that said,")
- Flag but do not silently fill unfilled placeholders: if a placeholder cannot be inferred from context, replace it with a clearly visible marker like [NEEDS INPUT] so the user knows it requires attention; if the placeholder can reasonably be inferred (e.g. a company name used earlier in the document), fill it in
- Preserve the original meaning, structure, and tone of the document — only change what is flagged above

# OUTPUT INSTRUCTIONS
- If the input was a file path: overwrite the file at that path with the corrected content, then output only a single confirmation line: "Fixed: <file path>"
- If the input was raw text: output only the corrected text — no preamble, no issue list, no commentary, no explanation
- Do not mention what was changed
- Do not add any closing remarks or offers to help further

# INPUT
$ARGUMENTS

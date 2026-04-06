---
name: ai-cleanup
description: Audits a document or text for AI-generated content patterns, LLM prompt leakage, and unfilled placeholders, then outputs a bullet-point list of findings with guidance on how to fix each issue.
disable-model-invocation: true
argument-hint: "<paste document text or file path>"
---

# PURPOSE
Analyze a user-provided document or text and flag three categories of issues:
1. AI-generated content markers (em-dashes, verbose/unnatural phrasing, overly formal or complex word choices no human would naturally write)
2. LLM prompt leakage — sentences that sound like the model talking back to the user (e.g. "If you want I could rewrite this", "Let me know if you'd like me to expand on this", "That said, if you prefer a different tone...")
3. Unfilled placeholders — tokens the user forgot to replace (e.g. TODO, [INSERT LINK], "put screenshot here", "fill in here", "[Company Name]", "[DATE]")

# STEPS
- Read the full document provided by the user
- Scan for AI content markers: em-dashes used as stylistic separators (— or --), words/phrases that are unusually formal or complex for the context (e.g. "delve", "underscore", "it is worth noting that", "in the realm of", "leverage", "navigate", "tapestry", "nuanced"), overly structured bullet lists that feel machine-generated
- Scan for LLM bleed-through sentences: any phrase where the text appears to address the reader as if offering further assistance, suggesting rewrites, or acknowledging the output was generated (e.g. "feel free to", "let me know if", "if you'd like", "I could also", "would you like me to", "that said,")
- Scan for unfilled placeholders: ALL-CAPS tokens like TODO or FIXME, bracketed tokens like [LINK], [NAME], [DATE], inline instructions like "add screenshot here", "insert image", "fill in", "put X here"
- Compile all findings into a structured bullet list grouped by category

# OUTPUT INSTRUCTIONS
- Group findings under three headings: **AI Content Markers**, **LLM Prompt Leakage**, and **Unfilled Placeholders**
- For each finding, quote the exact offending text and explain why it is flagged
- After each finding, add a short "Fix:" line telling the user exactly what to do
- If a category has no issues, write "None found." under that heading
- End with a short summary: total issues found and an overall verdict (Clean / Needs minor cleanup / Needs significant cleanup)
- Be direct and specific — do not hedge or soften findings

# INPUT
$ARGUMENTS

---
name: math-paper-writer
description: "Draft, extend, and revise English-language mathematical manuscripts and LaTeX proofs. Use for a proof write-up, theorem, section, or paper in a specified or existing style. Prefer displayed definitions, maintain a notation glossary, and verify affected arguments and references."
---

# Mathematical manuscript writing

Apply this workflow when a mathematical result, argument, or statement is ready to put into a manuscript. If the task includes exploration, apply the workflow when there is a result or a precise open claim to write down. Check definitions, proof dependencies, and source notes as you draft or revise each affected statement. Read [Research and verification](references/research-and-verification.md) for the applicable objective, proof, attribution, and build checks.

## Prepare the edit

- Read the affected manuscript sections and the surrounding definitions, statements, and proof dependencies before editing. Check the relevant macros, bibliography, and build instructions. Read a notation macro's definition before reusing it, especially if it acts as a relation.
- Treat each addition as new writing and each edit to existing text as a revision, including when the same task involves both. Preserve the model, assumptions, statements, estimates, notation, and citation keys unless the user requests changes to them. Follow the manuscript's file structure when integrating changes. Report any gap outside the edit's scope at its exact location.
- Write manuscript prose, footnotes, captions, source comments, and glossary entries in English. Preserve names and bibliography titles as published. Use the user's language for discussion.

## Follow the specified style

Follow the user's choice of journal, author, house style, or exemplars. Use project style instructions where the user's choice leaves room. Read the relevant instructions or exemplars before applying them. Within applicable venue requirements, follow the chosen author's conventions in the areas they cover and the target journal's patterns for the rest. In the absence of specified guidance, follow the existing manuscript or use concise mathematical prose for a new draft.

- Read the [probability journal style example](references/probability-journal-style.md) if it is selected or relevant to the specified target venue. Use the example for editorial patterns. Take mathematical claims and assumptions from the manuscript and verified sources.
- Read the [author style example](references/example-author-style.md) when it is selected as an exemplar. For a different author, use that author's supplied style notes or sample papers.
- If a requested style source is unavailable, use the available instructions and existing manuscript conventions. State which style source you used and identify any material choice that remains uncertain.

## Draft statements and proofs

1. Identify the exact statement and assumptions before writing the proof. For an estimate, identity, or limit, state the target formula where it helps the reader see what the argument must establish.
2. Define substantive objects before use and reuse existing notation. Prefer a centered display for a new or materially rewritten definition, especially for indexed objects, events, and counting variables. Use the manuscript's display environments and any alignment prescribed by its class. A short, unambiguous definition or local alias may be inline. Introduce the parts of imported definitions that the argument needs. State relevant ranges and moment conditions as formulas and specify types, laws, and conditioning when they affect the argument.
3. Keep the proof traceable from statement to conclusion. For a statement with multiple parts, make clear which passage proves each part. Expand compressed chains of estimates, conditioning arguments, or case splits where the justification is material. Cite the precise theorem, lemma, or equation when the reader needs an internal pointer. Verify new or changed mathematical reasoning and give source notes for key methods as described in the research reference.
4. If the available mathematics and conventions leave a choice that changes the claim or proof, identify the alternatives and their consequences. Ask only when that material choice remains unresolved. Continue with independent work and record the exact unresolved claim or definition in the glossary and handoff.

## Number displays and statements

Use unnumbered displays, such as `\[...\]`, for definitions and calculations used locally. Give a new display a label and a number when it needs a stable cross-reference. Preserve existing labels and printed equation and theorem numbers, including downstream numbering when adding text to an existing manuscript. If the fact already has a label, reuse that reference. For a new cross-reference, use a numbering convention the manuscript supports. If a required numbered addition would shift existing numbers, flag the conflict and proceed with other edits. When renumbering is authorized, update affected references and glossary locations and verify the compiled numbers.

## Maintain the glossary

For file-based writing, load or create `<manuscript-base>.glossary.md` beside the root manuscript unless the project or user specifies another location or format. Reuse an existing glossary's structure and entries. Update it in the same edit when a definition, symbol, first use, or anchor changes.

- For notation, record the symbol, meaning, type, definition location, and first use.
- For recurring verbal terms, record the term, its symbol or definition anchor, and its status. Use an existing label where available. For inline definitions or unnumbered displays, give the containing section or statement and enough context to locate the definition. Verify any printed numbers against the build.
- Record material choices about meaning or notation and the reason for them. Mark unresolved terms or claims as open.
- For a chat-only write-up, include the relevant new or changed glossary entries with the text.

## Deliver the write-up

Integrate in-scope changes in the existing files and compile using the applicable build checks in the research reference. Deliver the revised manuscript or requested LaTeX excerpt with the relevant glossary updates. Identify unresolved mathematical or source questions and any verification or build steps still pending.

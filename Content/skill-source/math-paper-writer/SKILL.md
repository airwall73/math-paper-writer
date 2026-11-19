---
name: math-paper-writer
description: "Draft, extend, and revise English-language mathematical manuscripts and LaTeX proofs. Give textbook-clear accounts of mathematical objects, constructions, and deductions in the requested style. Maintain notation and verify affected arguments and references."
---

# Mathematical manuscript writing

Use this workflow once there is a result or a precise open claim to write down. Apply the relevant proof, attribution, and build checks in [Research and verification](references/research-and-verification.md).

## Prepare the edit

- Read the affected manuscript sections and the proofs that depend on them. Check the relevant macros, bibliography, and build instructions. Read a notation macro's definition before reusing it, especially if it acts as a relation.
- Preserve the model, assumptions, statements, estimates, and citation keys unless the user requests changes to them. Reuse established notation and name any additional objects needed to state the argument. Follow the manuscript's file structure when integrating changes. Report any gap outside the edit's scope at its exact location.
- Write manuscript prose, footnotes, captions, source comments, and glossary entries in English. Preserve names and bibliography titles as published. Use the user's language for discussion.

## Follow the specified style

Read the requested journal instructions or author samples. Within venue requirements, follow the chosen author's conventions where specified and the journal's elsewhere. Use project style notes to fill gaps. Otherwise follow the existing manuscript, or use concise mathematical prose for a new draft. If a requested source is unavailable, say what you used and which material choices remain uncertain.

Use the [probability journal example](references/probability-journal-style.md) or [author example](references/example-author-style.md) when it fits the requested style. On rereading a draft, check doubtful technical phrasing in a primary paper that uses the same construction, preferably one already cited. Read the passage for the objects and conditions it describes. Use its wording only where the manuscript supports the same relation.

## Define the objects used in the proof

Write for a mathematician who knows the prerequisites and is seeing this construction for the first time. At its first substantive use, including in a section opening, carry out the construction from known objects. Define a recurring construction once in the main text. Introduce a short name afterwards if the reader will use it again.

- Use existing objects and indices to say what is chosen or in what order to proceed. Define an indexed family alongside its ambient object when individual members enter the proof. If two index systems occur, give their correspondence.
- Even familiar words need a local meaning when they determine a calculation. For a group give its membership rule and boundaries. For a relative position specify where counting starts (including whether the first member has index 0 or 1). For a distance give the reference point and unit. A short inline definition suffices when it determines the object.
- In a multistep definition, pause where the next operation uses a set or endpoints just chosen, or changes what is being counted. Show that intermediate result before continuing. For a sum, give its index set and summands. For a recursion, give the starting data and update. Display a substantial formula when it lets the reader check a step.
- If an adjective carries a probabilistic assertion, write the assertion. State which quantities are independent of which others, given what information, or specify the law or measurability the argument uses. An unobserved variable may depend on observed data. When conditioning or selecting observations changes the law, give the original law, the event or selection rule, and the probability or expectation identity actually used.
- When changing representation, state and justify the identity, equivalence, or approximation (with its error regime) that connects it to the original. Make domains and representative choices explicit when they affect the result.

For instance, the contribution of a cell $D_j$ to $\int_A f\,d\mu$ is $\int_{D_j\cap A} f\,d\mu$. To define an induced map on cosets, write $\bar L(v+M)=Lv+N$ and use $L(M)\subseteq N$ to check independence of the representative.

## Draft statements and proofs

1. Identify the exact statement and assumptions before writing the proof. For an estimate, identity, or limit, state the target formula where it helps the reader see what the argument must establish.
2. For a statement with multiple parts or a proof by cases, make clear which passage establishes each conclusion. In a derivation, put routine algebra in the formula and attach each substantive reason to the equality, inequality, or limit it justifies. Similar steps in parallel cases can use the same wording. See the [worked derivation](references/example-author-style.md#worked-derivation) for an example. Cite the precise result at the step that needs it. Verify new or changed reasoning and give source notes as described in the research reference.
3. Use a labeled lemma for a substantive fact or bound that several proofs need. A lemma used once can also help when its conclusion is easy to apply and stating it separately lets the reader set aside a lengthy construction. Give its hypotheses and conclusion, prove it once, and identify how its hypotheses are met where it is used. For a direct application of a published theorem, cite it in place with its locator if one sentence identifies the exact conclusion used and shows why the assumptions hold. When a special form needs separate statement or repeated use, give that form as a lemma with the source locator, normalization, and any argument needed to adapt it.
4. If the available mathematics and conventions leave a choice that changes the claim or proof, identify the alternatives and their consequences. Ask only when that material choice remains unresolved. Continue with independent work and record the exact unresolved claim or definition in the glossary and handoff.

## Number displays and statements

Use unnumbered displays, such as `\[...\]`, for local definitions and calculations. A labeled lemma can anchor an unnumbered display in its statement. Preserve existing labels and printed equation and theorem numbers, including downstream numbering when adding text to an existing manuscript. Reuse the existing label when promoting a formula into a lemma. For new references, use a compatible numbering convention, such as a letter suffix where appropriate. If a required numbered addition would shift existing numbers, flag the conflict and proceed with other edits. When renumbering is authorized, update affected references and glossary locations and verify the compiled numbers.

## Maintain the glossary

For file-based writing, load or create `<manuscript-base>.glossary.md` beside the root manuscript unless the project or user specifies another location or format. Reuse an existing glossary's structure and entries. When the glossary is unavailable, reconstruct the entries needed for the edit from the manuscript and its downstream uses. Update them in the same edit when a definition, symbol, first use, or anchor changes.

- For notation, record the symbol, meaning, type, definition location, and first use. Compare indexed families that are in scope together: substitute the same admissible index in both and read the printed expressions. If $R_j$ counts the right subtrees at level $j$ and $R_n$ counts the distinct sites visited in $n$ steps, both definitions assign a meaning to $R_1$. Keep the established notation for the principal quantity and give the auxiliary family a distinct name or symbol throughout its uses. If a rename would extend beyond the edit, flag both definitions.
- For recurring verbal terms, record the term, its symbol or definition anchor, and its status. Use an existing label where available. For inline definitions or unnumbered displays, give the containing section or statement and enough context to locate the definition. Verify any printed numbers against the build.
- Record material choices about meaning or notation and the reason for them. Mark unresolved terms or claims as open.
- For a chat-only write-up, include the relevant new or changed glossary entries with the text.

## Deliver the write-up

Read the passage in order. Cover the name of each new construction and use the preceding text to perform it. Substitute the result into its first dependent formula, checking indices, restrictions, and the hypotheses it uses. For a grouping, count, or relative position, try a small admissible input where a boundary matters (for example, the first member or an empty group). If two readings give different values, identify the missing convention and check the rest of the argument for it. If the mathematics leaves it open, report the alternatives under the proof rule above.

Integrate in-scope changes in the existing files and compile using the applicable build checks in the research reference. Deliver the revised manuscript or requested LaTeX excerpt with the relevant glossary updates. Identify unresolved mathematical or source questions and any verification or build steps still pending.

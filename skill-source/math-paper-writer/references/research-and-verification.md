# Research and verification

Apply the sections relevant to the requested work. These checks also apply to standalone mathematical investigations and proof reviews.

## Objective

At the start of a substantial task, identify the precise objective, the statement or estimate at issue, and the completion criterion. Work these out from the problem and manuscript when needed. Preserve the user's original objective, model, and assumptions. Proceed with work already authorized.

## Mathematical checks

- Independently rederive symbolic calculations that support a new or materially changed argument, or that are in scope for verification. Check asymptotic expansions, the regimes and uniformity of error bounds, and degenerate and boundary cases where relevant.
- Prefer exact arithmetic whenever possible. When the work relies on computation, provide reproducible scripts or commands and record dependencies and assumptions. For formal verification, name the exact formalized statement and the assumptions it uses.
- Report the status of each result at the level of the exact statement the work establishes. Treat numerical checks as evidence only. If a theorem uses a formally verified lemma, name the lemma and give the status of the theorem. Mark gaps as open and identify the missing argument or estimate and the assumptions under which it is needed.

## Attribution

Verify primary sources for the constructions and methods that drive the proof structure, a key estimate, or identification of a limit. At the first substantive use, add a compilable LaTeX footnote in nearby prose. Give a full source note once for each method and cross-reference it later where useful.

- For a directly used result or construction, give the author, citation key, and a verifiable section, theorem, or equation number. State the exact form used in the manuscript's notation. Show in the proof how the hypotheses are met.
- For an adaptation, identify the step borrowed, what changes here, and the estimate or justification the new proof still needs. Spell out differences in conditioning, time window, normalization, or limiting object when relevant. If the argument uses an equivalent reformulation of a source definition or result, justify the equivalence it relies on.
- For an analogy, identify the shared mechanism and the scope of the analogy. For an independent derivation, name the standard tools that justify it. If a source or locator remains unverified, mark it as pending and record what material was checked. Keep provisional notes compilable with the available citation keys.

For manuscript edits, place the footnote in the source and add the verified bibliography entry if needed, using the project's citation conventions and existing keys. For a proof written only in chat, put a paste-ready LaTeX footnote after the corresponding proof passage and provide the bibliography entry if its key is new and verified.

## Build and inspect

- Use the manuscript's documented build command, engine, and bibliography workflow when available. Otherwise, infer the engine from the source and use the available tools. Build until affected references stabilize and fix actual compilation errors within scope.
- Check affected citations, footnotes, labels, and printed theorem and equation numbers. Compare with the prior output if the edit could shift existing numbering. Inspect the affected PDF pages when rendering is available.
- If source access, compilation, or rendering is unavailable, deliver the work the environment supports and identify the specific checks still pending.

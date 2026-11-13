# math-paper-writer

[![lang-中文](https://img.shields.io/badge/lang-%E4%B8%AD%E6%96%87-red?style=for-the-badge)](README.md)
[![lang-English](https://img.shields.io/badge/lang-English-blue?style=for-the-badge)](README.en.md)

A skill package that makes AI write **rigorous, readable, and verifiable mathematical proofs**.
Designed for GPT 6 Astra; works with other LLMs and agent harnesses as well.
It constrains only the writing and verification workflow — **it does not change the proof logic itself**.

## Usage

**One-off / web version**: drop the zip onto the AI, e.g.

```
Following this package's conventions, prove that there are infinitely many primes.
```

or

```
Following this package's conventions, rewrite xxx.tex
```

**Long-term / Codex-style agents**: put the contents of the Content folder into your **workspace**, and the AI will pick it up automatically. The package consists of an `AGENTS.md` and a skill — if the workspace already has an `AGENTS.md`, merge the two texts. Note that one deployment applies to **a single workspace** only.

## Before / after example

The same lemma (from a manuscript on tree-indexed random walks), comparing the AI's native write-up with the one produced under this skill.

**Before** — everything compressed into a single paragraph, definitions and estimates buried in prose:

> **Lemma 2.2 (Attachment mixing).** The attachment environment indexed by individual right trees has an exponentially absolutely regular stationary renewal version. A translation-invariant function of $r$ ancestral levels can be localized to $h$ tree indices with exceptional probability at most $Ce^{-ch+Cr}$. The initial renewal environment has bounded density with respect to the stationary version, and admits an exponential coupling to it.

**After** — objects given as formal definitions first, conclusions split into numbered parts, key estimates displayed and numbered for cross-referencing:

> **Lemma 2.2 (Attachment mixing).** For $j \ge 1$ let $\mathcal{E}_j$ collect the right count $R_j$ and the shapes and spatial marks of the right trees at ancestral level $j$, and let $\nu_r$ be the number of tree indices in the renewal blocks constructed below that meet levels $1,\dots,r$, including the two boundary blocks.
>
> (i) Reindexed by tree index, $(\mathcal{E}_j)$ has a stationary renewal version $(\mathcal{E}^{\mathrm{st}}_j)$ and an exponential coupling to it:
>
> $$\mathbb{P}\bigl(\mathcal{E}_j \ne \mathcal{E}^{\mathrm{st}}_j \ \text{for some } j \ge n\bigr) \le Ce^{-cn}. \qquad (34)$$
>
> In particular it is absolutely regular with exponentially decaying coefficients.
>
> (ii) For $r, h \ge 1$,
>
> $$\mathbb{P}(\nu_r > h) \le Ce^{-ch+Cr}. \qquad (35)$$
>
> Hence a measurable function of $r$ consecutive level environments, applied at any starting level, agrees with a function of at most $h$ tree indices off an event of probability at most $Ce^{-ch+Cr}$, uniformly in the starting level.
>
> (iii) The initial renewal environment has bounded density with respect to the stationary version, and admits an exponential coupling to it.

## Appendix: a trick to stop the AI from slacking

GPT 6 Astra often advances one small step and then stops. Use the native `/goal` feature to lock in the finish line, e.g.

```
/goal Prove that there are infinitely many primes.
```

## Feature details

### 1. The AI audits itself

Inspired by the design of grill-with-docs, but the focus is not human–AI reconciliation — the AI reconciles with itself:

- Maintains a **notation/terminology glossary** (`glossary.md`): every symbol records its meaning, type, definition location, and first use; any term the AI invents must have a corresponding symbol and anchor; unresolved entries are marked as open
- Every statement's dependencies come with precise theorem/lemma/equation number pointers

### 2. Displayed definitions

Important definitions are set as centered displays, not buried in dense prose.

### 3. Source-attribution footnotes

For methods that drive the proof structure, a key estimate, or the identification of a limit, a footnote is added at first use:

- Direct use → author, citation key, and a verifiable section/theorem number, with the hypotheses checked in the proof
- Adaptation → which step is borrowed, what changes here, and what estimate still needs to be supplied
- Analogy / independent derivation → the shared mechanism or the standard tools being invoked
- Unverified sources are marked as pending — no pretending they were checked

### 4. Journal style adaptation

- Built-in probability journal style sample (based on AOP, PTRF, and other probability journals): abstract and introduction conventions, theorem placement, proof roadmap, when remarks earn their place, etc.
- Can be swapped for a journal you specify, and an author style can be added (takes a bit of DIY: just ask the agent to fetch samples from your arXiv page or personal homepage and add them to this skill)

### 5. Mathematical verification workflow

- Newly written or materially changed derivations are **independently re-checked**; asymptotic regimes, uniformity of error bounds, and degenerate/boundary cases are examined
- Exact arithmetic is preferred; when computation is used, reproducible scripts/commands are provided
- Numerical checks count as evidence, not proof; gaps are honestly marked as open

### 6. Other conventions

- **Writes in English only** (main text, footnotes, glossary entries) — independent of the language you use in chat
- Numbering discipline: local definitions/calculations use unnumbered displays `\[...\]`; numbers are assigned only when a stable cross-reference is needed; existing equation and theorem numbers are preserved
- Long tasks maintain a checkpoint (objective, established results, open statements, failed approaches, next steps) so work can resume seamlessly
- While the main problem is open, prioritize the critical obstruction over polishing and recompiling

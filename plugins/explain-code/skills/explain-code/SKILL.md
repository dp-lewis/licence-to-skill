---
name: explain-code
description: Explain a file or the currently selected code in plain language. Use when someone asks "what does this do?", is onboarding to an unfamiliar area of the codebase, or wants a walkthrough of a function, module, or config file.
argument-hint: "[file-or-symbol]"
---

# Explain code

Produce a clear, plain-language explanation of the target code. The goal is
understanding, not a line-by-line paraphrase.

## Steps

1. **Find the target.** If an argument was given (`$ARGUMENTS`), explain that
   file or symbol. Otherwise explain the currently selected code or, if nothing
   is selected, the most recently discussed file. Read it before explaining —
   never guess from the name.
2. **Lead with the purpose.** Open with one or two sentences on what this code
   is *for* and where it fits in the wider system.
3. **Walk the important parts.** Cover the key functions, types, and control
   flow. Group related lines; skip boilerplate. Reference concrete
   `path:line` locations so the reader can follow along.
4. **Call out what matters.** Note any non-obvious behaviour, side effects,
   edge cases, error handling, or assumptions a reader could trip over.
5. **Keep it proportional.** A short helper needs a short explanation. Don't
   pad, and don't invent complexity that isn't there.

## Style

- Assume a competent engineer who is simply new to *this* code.
- Prefer prose and short lists over restating the source verbatim.
- If something is genuinely unclear or looks like a bug, say so plainly rather
  than smoothing over it.

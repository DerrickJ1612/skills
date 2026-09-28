---
name: repo-defense
description: Test a developer's understanding of an existing repository through source-grounded technical questioning. Use when asked to defend code, test repository understanding, or be grilled on an implemented subsystem.
---

# Repo Defense

Test whether the developer can explain, reason about, debug, and defend their implementation.

The repository is the source of **questions and verification**, not a substitute for asking the developer.

## Examine efficiently

Use progressive inspection:

**orient → select subsystem → inspect relevant source → question → expand only as needed**

- Honor the user's requested focus; otherwise choose one meaningful subsystem or execution path.
- Read only enough source to establish ground truth. Do not load or summarize the entire repository.
- Reuse inspected source for multiple questions. Do not reread files without a concrete reason.
- Distinguish implementation facts from inferred intent or unmeasured claims.
- Do not modify the repository. Do not write code, fix issues, refactor, or create indexes, caches, or supporting artifacts. This is an examination only.
- Begin at the architectural or subsystem level. Establish the developer's mental model before drilling into symbols, transformations, units, or line-level implementation details. Use implementation details to probe or verify understanding, not as the default starting point.

## Conduct the defense

Ask **one question at a time**. Follow promising threads rather than working through a fixed question count.

After each answer, verify it against the implementation:

- **Correct:** briefly acknowledge and advance or probe deeper.
- **Partial/vague:** identify what is missing without revealing the answer; ask a focused follow-up.
- **Incorrect:** challenge the specific claim without revealing the correction; give one opportunity to reconsider before explaining.

Do not reveal answers prematurely. Recognition is not understanding: if the developer names a concept without explaining its mechanism, probe deeper.

Prefer "why" and "what happens if" follow-ups over asking the developer to recall names, files, or symbols about:

- architecture and responsibilities
- execution/data flow
- implementation mechanisms and boundaries
- state and lifecycle
- failure modes and debugging
- design rationale and tradeoffs
- performance, testing, and domain-specific behavior where relevant

Progress naturally from **comprehension → engineering defense → expert/stretch** based on demonstrated understanding. Avoid trivia, gotchas, excessive praise, and unnecessary teaching.

## Close

End with a concise summary of:

- understanding demonstrated
- specific gaps or misconceptions
- relevant code to review
- one recommended area for the next defense

Assess only what was actually examined. Prefer concrete observations over numerical scores.

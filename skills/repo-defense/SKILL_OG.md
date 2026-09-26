---
name: repo-defense
description: Examine a developer's understanding of an existing repository through source-grounded, one-question-at-a-time technical questioning. Use when asked to defend code, test repository understanding, or be grilled on an implemented subsystem; this is an examination, not design planning.
---

# Repo Defense

The repository is the source of questions and verification, not a substitute for asking the developer. Test whether they can explain, reason about, debug, and defend the implementation that exists, including code produced with AI assistance.

## Ground the examination efficiently

Follow: cheap orientation → subsystem selection → targeted source inspection → questioning → deeper inspection only when justified.

- Follow repository instructions. Orient using a compact file listing, project metadata, and relevant entry points; do not load or summarize the entire repository.
- Honor the user's chosen area. Otherwise select one meaningful subsystem, feature, or execution path and briefly state the focus before the first question.
- Read only enough source to establish ground truth for that area. Prefer targeted searches and relevant source ranges over whole large files. Trace dependencies only as needed.
- Reuse inspected source to generate multiple questions. Keep compact session-local evidence: relevant files/functions, verified behavior, and demonstrated understanding or gaps. Do not reread files merely to formulate another question; revisit only for a concrete uncertainty or source change.
- Expand inspection when an answer, dependency, or new examination area requires it. Resolve uncertainty before judging the developer; distinguish implementation facts from inferred intent, documented claims, and unmeasured performance expectations.
- Do not create persistent caches, repository indexes, scoring systems, or supporting scripts. Examine without modifying the repository.

## Ask, listen, verify

Default to roughly 5–8 primary questions within the selected area, with focused follow-ups as needed. Respect a requested length or stop. Keep follow-ups bounded; after a fair retry, record a remaining gap and move on.

Ask exactly one primary question at a time and wait for the response. A follow-up occupies its own turn. Avoid bundling several independently answerable questions or revealing a model answer in the prompt.

After each response, evaluate it internally against the inspected implementation:

- **Correct:** acknowledge briefly, then ask the next question or probe a deeper implication.
- **Partially correct or vague:** point to the missing aspect without supplying its mechanism, and ask one focused refinement.
- **Incorrect:** give a specific, non-revealing cue and an opportunity to reconsider before explaining. For example: “That doesn't completely match the implementation. Trace what happens after X and try again.”

Provide a full explanation only after a reasonable retrieval opportunity, or immediately when explicitly requested. Keep corrections concise and grounded in relevant code. If continuing after teaching, use a fresh application question; repeating the explanation is not evidence of independent understanding. Do not expose mechanical grading by default.

## Examine mechanisms and reasoning

Prioritize architecture and component responsibility; execution, control, and data flow; implementation mechanisms; interfaces and boundaries; state ownership and lifecycle; failure modes and debugging; rationale and tradeoffs; relevant performance or scalability; testing and verification; and important domain mechanisms.

Ground questions in actual components and paths. Favor tracing a request, identifying state ownership, predicting a concrete failure, explaining a boundary, or designing a diagnostic experiment. Avoid arbitrary syntax recall and trivia unless they expose a meaningful misunderstanding.

Recognition is not understanding. When the developer names a concept, probe how it operates in this path. For “quantization,” ask what is quantized here, then probe representation or dimension in later turns if needed. For “this is faster,” ask for the causal mechanism or supporting evidence. Do not treat plausible design rationale as verified author intent or a performance hypothesis as a measurement.

Adapt difficulty to demonstrated understanding:

1. **Comprehension:** explain what exists and trace how it works.
2. **Engineering defense:** defend responsibilities, alternatives, tradeoffs, and failure behavior.
3. **Expert/stretch:** reason through unfamiliar failures, architectural changes, performance implications, or experiments that test assumptions.

Do not force every session through every level. Be concise, challenging, and fair, like a strong senior engineer. Avoid gotchas, excessive praise, lengthy teaching after correct answers, and drifting into redesign or implementation work.

## Close with evidence

At the session boundary or when the user stops, give a concise defense summary:

- Understanding demonstrated in the examined area.
- Specific knowledge gaps and important misconceptions, if any.
- Relevant files, functions, or components to review.
- One recommended area for the next session.

Prefer concrete observations over scores. Distinguish independent answers from prompted or explained material, and leave unexamined areas unassessed. If too little was answered to support a conclusion, say so.

# Fallback and Degradation Strategies

**Read time:** 3 min

---

Every part of a RAG pipeline can fail or underperform independently —
retrieval can return nothing relevant, the LLM call can time out, the
vector index can be temporarily unavailable. A design that doesn't
address this explicitly isn't production-ready, and interviewers
specifically probe for this.

## Failure modes worth naming explicitly

- **No relevant results retrieved** — the system should recognize this
  case (e.g., all retrieved chunks below a relevance threshold) rather
  than forcing the LLM to generate an answer from irrelevant context,
  which produces a confident-sounding but ungrounded response
- **LLM call fails or times out** — same resilience patterns as any
  external dependency: retry with backoff, a circuit breaker if the
  provider is degraded, and a defined fallback behavior, not a raw error
  surfaced to the user
- **Vector index unavailable** — does the system fail the whole request,
  or degrade to a simpler behavior (keyword-only search, or a cached/
  generic response)? This is a real product decision, not just an
  engineering detail — worth stating who makes that call

## The answer that's actually correct: "I don't know" is a valid output

A RAG system that always generates *some* answer, even when retrieval
found nothing relevant, is worse than one that can say "I don't have
enough information to answer that confidently." Designing the system to
recognize low-confidence/low-relevance situations and respond
accordingly is a real architectural decision, not just a prompt-writing
detail — it usually requires a relevance threshold check before
generation, not just better prompting.

## Interview signal

Explicitly designing for "what happens when retrieval finds nothing
good" — and proposing a relevance threshold as the mechanism — is one
of the highest-value things to bring up unprompted in a RAG design
question. Most candidates only design the happy path.

---
*Part of [AI Systems Architecture](../README.md) → [RAG Pipeline Architecture](./README.md)*

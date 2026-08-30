# Cost Architecture for AI Systems

**Read time:** 3 min

---

Unlike most backend components, AI inference cost scales directly with
*usage in a way that's visible per-request* (tokens in, tokens out) —
this changes how you think about architecture decisions that would be
cost-irrelevant elsewhere.

## The cost levers that actually matter

- **Model choice** — a larger/more capable model costs more per call;
  the architectural skill is routing different request types to
  appropriately-sized models rather than defaulting everything to the
  most capable (and most expensive) option
- **Prompt/context length** — every token in the context window costs
  money on most pricing models; RAG retrieval quality directly affects
  cost here (retrieving more chunks "to be safe" has a real cost, not
  just a latency one)
- **Caching repeated queries/responses** — semantically identical or
  near-identical requests are common in real usage; caching avoids
  re-paying for inference on the same effective question
- **Output length control** — unconstrained generation length is a real,
  often-overlooked cost lever

## The architectural pattern this leads to: model routing

A tiered approach — a cheap, fast model handles simple/high-confidence
requests, escalating to a more expensive model only when needed
(complexity detected, low confidence, or explicit user request for
deeper reasoning). This is directly analogous to caching strategies in
traditional systems: don't pay full cost for something you don't need
full capability for.

## Interview signal

If a design question involves scale ("what if this had 10x traffic"),
bringing up cost architecture unprompted — not just latency and
throughput — signals you're thinking about the system as something that
has to be *operated*, not just built. Most candidates only get asked
about cost explicitly; mentioning it proactively is a differentiator.

---
*Part of [AI Systems Architecture](../README.md) → [AI Application Architecture Fundamentals](./README.md)*

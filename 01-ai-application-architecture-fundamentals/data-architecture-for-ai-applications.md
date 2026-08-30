# Data Architecture for AI Applications

**Read time:** 3 min

---

AI applications add a genuinely new data architecture concern beyond
traditional systems: data doesn't just need to be stored and queried, it
often needs to be transformed into a form a model can use effectively —
embeddings, structured context, fine-tuning datasets.

## The data layers specific to AI applications

- **Source data** — the original documents, records, or content, stored
  same as in any traditional system
- **Processed/derived data** — chunked, cleaned, embedded versions of
  source data, purpose-built for retrieval (the full mechanics live in
  [RAG Pipeline Architecture](../02-rag-pipeline-architecture) — this doc
  is the "what layers exist" overview, that section is the "how each one
  works")
- **Vector storage** — embeddings need a store optimized for similarity
  search, not a traditional relational or document store's strengths
- **Feedback/evaluation data** — logged interactions, corrections, and
  quality signals, which become the input for improving the system over
  time — often the most-neglected layer in a first-pass architecture

## The freshness problem, stated explicitly

Unlike a traditional cache, a stale vector index doesn't just serve old
data — it can cause the AI component to reason confidently about facts
that are no longer true. Data architecture for AI applications needs an
explicit answer to "how fresh does this need to be, and what's the
re-indexing/update strategy" — treating it as a solved problem by default
is a common design gap.

## Interview signal

A common trap: describing an AI feature's data flow purely in terms of
the source database, without ever mentioning the derived/processed layer
(chunking, embeddings) or how it stays in sync with the source. Naming
that sync problem explicitly — "here's how the vector index stays
current when source documents change" — is a concrete signal of having
actually operated one of these systems, not just read about them.

---
*Part of [AI Systems Architecture](../README.md) → [AI Application Architecture Fundamentals](./README.md)*

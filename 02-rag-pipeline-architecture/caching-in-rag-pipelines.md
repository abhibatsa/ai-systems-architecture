# Caching in RAG Pipelines

**Read time:** 3 min

---

RAG pipelines have more caching opportunities than a typical backend
system, because there are multiple expensive steps in sequence — and
each one is a candidate for caching independently.

## Where caching applies in the pipeline

- **Embedding cache** — the same query text embedded twice shouldn't
  recompute the embedding; cache query embeddings keyed by the query
  text (or a normalized version of it)
- **Retrieval cache** — for genuinely repeated or near-duplicate
  queries, cache the retrieved chunk set itself, skipping the similarity
  search entirely on a cache hit
- **Full response cache** — for exact or near-exact repeated queries,
  cache the final generated response — the biggest cost/latency win, but
  also the riskiest if the underlying source data changes and the cache
  isn't invalidated

## The freshness trade-off, specific to RAG caching

Unlike caching a static asset, a cached RAG response can become
*confidently wrong* if source data changed after the cache was
populated — this is a sharper version of the general
[cache invalidation](https://github.com/abhibatsa/architecting-software/blob/main/01-system-design-and-architecture/01-core-concepts/caching-patterns-and-invalidation.md)
problem, because a stale AI-generated answer doesn't look stale — it
looks like a normal, confident response.

## A practical pattern: semantic cache keys

Exact-string cache keys miss a lot of real-world value, since users
phrase the same question many different ways. A semantic cache — keyed
by embedding similarity rather than exact text match, with a similarity
threshold for what counts as "the same question" — catches near-duplicate
queries that an exact-match cache would miss entirely.

## Interview signal

Mentioning caching at all in a RAG design (many candidates don't) is a
positive signal; mentioning the *specific* freshness risk — that a stale
RAG cache is more dangerous than a stale static-content cache because
it's silently wrong, not visibly outdated — is a stronger one.

---
*Part of [AI Systems Architecture](../README.md) → [RAG Pipeline Architecture](./README.md)*

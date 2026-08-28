# AI Systems Architecture

**architecting-software's AI-native counterpart** — same "requirement to
production" rigor, same trade-offs-and-failure-modes format, applied to
systems that didn't exist as a category five years ago: RAG pipelines,
agentic AI, multi-agent orchestration, LLM serving, multimodal and voice
AI, and the guardrails that keep all of it safe to ship.

## Where this repo sits relative to its siblings

This is a genuinely distinct discipline from three repos it's easy to
confuse it with — worth being precise about the boundary rather than
letting content blur across them:

| Repo | Layer | This repo isn't that because |
|---|---|---|
| [`rnd-ai-ml-llm`](https://github.com/abhibatsa/rnd-ai-ml-llm) | **Theory** — how attention works, what RAG conceptually is | This repo is the "how you build and scale it in production" layer on top of that theory — same relationship as physics to structural engineering |
| [`architecting-software`](https://github.com/abhibatsa/architecting-software) | **Classical distributed systems** — databases, APIs, caching, sharding | Deliberately scoped to general system design; AI-native architecture gets its own repo instead of blurring that one |
| [`ai-test-engineering-career-prep`](https://github.com/abhibatsa/ai-test-engineering-career-prep) | **Testing** AI systems after they exist | This repo is architecture — designing the thing before it's built, not evaluating it after |

Cross-linked throughout, never duplicated: theory pointers go to
`rnd-ai-ml-llm`, testing pointers go to `ai-test-engineering-career-prep`,
tool-usage pointers go to
[`ai-tools-mastery-academy`](https://github.com/abhibatsa/ai-tools-mastery-academy).

## 🗺️ Structure

| # | Section | Covers |
|---|---|---|
| 01 | [AI Application Architecture Fundamentals](./01-ai-application-architecture-fundamentals) | Where AI fits in product architecture, sync/async inference, cost architecture, build vs. buy |
| 02 | [RAG Pipeline Architecture](./02-rag-pipeline-architecture) | Retrieval design, chunking, hybrid search, caching, fallback behavior |
| 03 | [Agentic AI & Multi-Agent Systems](./03-agentic-ai-and-multi-agent-systems) | Orchestration patterns, tool-calling, memory/state, failure isolation |
| 04 | [LLM Serving & Inference Architecture](./04-llm-serving-and-inference-architecture) | Deployment patterns, latency/throughput, serving infrastructure (incl. vLLM-style engines), quantization |
| 05 | [Multimodal & Vision-Language Architecture](./05-multimodal-and-vision-language-architecture) | Vision-language model architecture, multimodal pipeline design |
| 06 | [Voice AI Architecture](./06-voice-ai-architecture) | STT/TTS pipeline design, latency-critical real-time audio |
| 07 | [AI Automation & Agent Workflows](./07-ai-automation-and-agent-workflows) | Designing automation systems that use AI as a component, human-in-the-loop patterns |
| 08 | [Guardrails & AI Safety Architecture](./08-guardrails-and-ai-safety-architecture) | Architecting the safety layer — distinct from testing it |
| 09 | [Real-World Case Studies](./09-real-world-case-studies) | Full requirement-to-production write-ups, same template as the flagship repo |
| 10 | [Interview Prep](./10-interview-prep) | AI systems design interview framework, common questions indexed |

## A note on scope decisions

"XLLM" and "VLLM" were part of the original ask for this repo without a
confirmed definition — VLLM is covered under both plausible readings
(Vision-Language Models in §05, vLLM-style serving engines in §04);
"XLLM" (extended/specialized LLM variants) is folded into §04 rather than
given its own section, since it wasn't scoped precisely enough to justify
one. Flag if that's wrong and it'll move.

## 📇 Related repos in this family

- [R&D — ML, DL, AI & LLMs](https://github.com/abhibatsa/rnd-ai-ml-llm) — theory layer underneath this repo
- [System Design & Architecture](https://github.com/abhibatsa/architecting-software) — this repo's classical-systems counterpart
- [AI Test Engineering Career Prep](https://github.com/abhibatsa/ai-test-engineering-career-prep) *(private)* — testing what this repo teaches you to build
- [AI Tools Mastery Academy](https://github.com/abhibatsa/ai-tools-mastery-academy) *(private)* — tool usage, not architecture

## 🤝 Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md).

## 📄 License

MIT

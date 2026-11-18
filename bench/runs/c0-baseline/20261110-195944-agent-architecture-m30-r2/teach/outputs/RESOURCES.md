# Agent architecture Resources

## Knowledge

- [Article: "Effective context engineering for AI agents" (Anthropic Engineering)](https://anthropic.com/engineering/effective-context-engineering-for-ai-agents)
  Primary source on context as a finite resource, compaction, structured notes and just-in-time retrieval. Use for: O3 and any decision about what an agent keeps in context.
- [Paper: "Lost in the Middle: How Language Models Use Long Contexts" (Liu et al., TACL 2024)](https://ar5iv.labs.arxiv.org/html/2307.03172)
  Shows models use information at the start and end of a long context better than the middle. Use for: arguing against stuffing the window.
- [Article: "What is a context window?" (Designveloper)](https://www.designveloper.com/blog/what-is-a-context-window/)
  Secondary plain-language explainer of tokens and the window. Use for: a quick definition; confirm limits in provider docs.

## Wisdom (Communities)

- Local: the makerspace staff. Use for: real student questions to test where each answer would live.

## Gaps

- Provider documentation on token pricing and prompt caching, not yet read; needed for budget estimates.

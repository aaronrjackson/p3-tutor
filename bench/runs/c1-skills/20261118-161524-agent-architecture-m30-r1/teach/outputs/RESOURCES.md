# Agent architecture Resources

## Knowledge

- [Article: "Effective context engineering for AI agents" (Anthropic Engineering, Sep 2025)](https://anthropic.com/engineering/effective-context-engineering-for-ai-agents)
  Defines context, context rot, just-in-time retrieval, compaction, note-taking and sub-agents. Use for: what to keep in context, and memory design for agents.
- [Docs: Context windows (Claude Platform)](https://platform.claude.com/docs/en/build-with-claude/context-windows)
  How each request carries the whole history, what counts toward the window, and what happens at the limit. Use for: cost and size questions.
- [Article: "Introducing Contextual Retrieval" (Anthropic, Sep 2024)](https://anthropic.com/news/contextual-retrieval)
  Chunks, embeddings, BM25, reranking, and the advice to skip retrieval for knowledge bases under 200,000 tokens. Use for: finding the right page in a long manual. Its numbers come from 2024 experiments with older models.
- [Docs: Memory tool (Claude Platform)](https://platform.claude.com/docs/es/agents-and-tools/tool-use/memory-tool)
  The memory tool is a client-side tool: the model asks, your program stores files. Seen in search results only (Spanish page); find the English page before relying on details.

## Wisdom (Communities)

- Local: your university makerspace staff and the students who ask the questions.
  Use for: real questions to test the assistant on, and which manual pages people really need.

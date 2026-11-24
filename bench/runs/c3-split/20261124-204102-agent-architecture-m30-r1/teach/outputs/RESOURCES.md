# Agent architecture Resources

## Knowledge

- [Article: "Effective context engineering for AI agents" (Anthropic Engineering)](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)
  First-party article on finite context, trimming and summarizing, notes outside the context, and just-in-time retrieval. Use for: what to keep in context, context rot, notes as memory.
- [Docs: Context windows (Claude Platform Docs)](https://platform.claude.com/docs/en/build-with-claude/context-windows)
  Official description of what counts toward the window and how each turn resends history. Use for: window limits, tool results in history, cost of input and output.
- [Docs: Glossary (Claude Platform Docs)](https://platform.claude.com/docs/en/about-claude/glossary)
  Short official definitions of token and RAG. Use for: what a token is, what retrieval does.
- [Docs: Memory tool (Claude Platform Docs)](https://platform.claude.com/docs/en/agents-and-tools/tool-use/memory-tool)
  Shows that the application, not the model, stores and runs memory files. Use for: notes between sessions, pruning, per-user storage.
- [Article: "Contextual Retrieval" (Anthropic)](https://www.anthropic.com/news/contextual-retrieval)
  Explains chunking, keyword and meaning search, and chunks that lose meaning. Use for: how to find the right page in a long manual.

## Wisdom (Communities)

- [LangChain Forum](https://forum.langchain.com)
  Discourse forum run by the LangChain team; "Talking Shop" covers building agentic applications. Use for: asking how others handle per-user notes and manual retrieval. It is tied to one framework.

## Gaps

- No opened source for "code and numbers often take many tokens", for a step limit as a way to keep context small, or for what chat apps save and resend.

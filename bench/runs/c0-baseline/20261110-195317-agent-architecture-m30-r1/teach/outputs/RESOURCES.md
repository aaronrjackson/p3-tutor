# Agent architecture Resources

## Knowledge

- [Article: "Effective context engineering for AI agents" (Anthropic Engineering)](https://anthropic.com/engineering/effective-context-engineering-for-ai-agents)
  Context window, context rot, compaction, note-taking, just-in-time retrieval. Use for: any decision about what an agent keeps in context.
- [Docs: Context windows (Claude API)](https://platform.claude.com/docs/en/build-with-claude/context-windows)
  Definition of the window, what counts toward it, how turns accumulate. Use for: cost and limit questions.
- [Docs: Memory tool (Claude API)](https://platform.claude.com/docs/en/agents-and-tools/tool-use/memory-tool)
  Client-side file memory across sessions. Use for: designing saved notes.
- [Paper: "Lost in the Middle" (Liu et al., TACL 2024)](https://ar5iv.labs.arxiv.org/html/2307.03172)
  Models use information at the start and end of long inputs better than the middle. Use for: arguing against pasting whole manuals.

## Wisdom (Communities)

- Local: makerspace staff and course instructors
  Use for: real student questions to test which need notes and which need retrieval.

## Gaps

- A high-trust source on retrieval design (chunking, embeddings) for manuals.

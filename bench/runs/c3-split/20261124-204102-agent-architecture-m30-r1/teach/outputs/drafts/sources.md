# Sources for the O3 lesson

## Primary source

- Link: https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents
- Title: Effective context engineering for AI agents (Anthropic Engineering)
- Reason: It is a first-party article that covers the whole lesson (finite context, trimming and summarizing, notes outside the context, just-in-time retrieval) in one place, and the Claude docs point to it.

## Claims

Short names: EA = effective-context-engineering article; CW = context windows doc; GL = glossary; CR = contextual retrieval; MT = memory tool doc.

1. A token is a small piece of text (word, part of a word, character). Plan: Section 1.
   - Link: https://platform.claude.com/docs/en/about-claude/glossary
   - Title: Glossary (Claude Platform Docs)
   - Support: "Tokens are the smallest individual units of a language model, and can correspond to words, subwords, characters, or even bytes." Earlier models: "a token represents approximately 3.5 English characters"; Claude 4.7 and later give "approximately 30 percent more tokens for the same text."
   - checked

2. A token is about 3/4 of an English word (rough rule). Plan: Section 1.
   - Not found in a Claude page I opened. The glossary gives 3.5 characters, not 3/4 word. See Gaps.

3. The context window is all the text the model can reference, including its own reply. Plan: Section 1.
   - Link: https://platform.claude.com/docs/en/build-with-claude/context-windows
   - Title: Context windows
   - Support: "The 'context window' refers to all the text a language model can reference when generating a response, including the response itself."
   - checked

4. The call holds instructions, tool descriptions, the question, the page and the answer, all in one limit. Plan: Section 1, Figure 1.
   - Link: https://platform.claude.com/docs/en/build-with-claude/context-windows
   - Title: Context windows
   - Support: "Everything in the request counts toward the context window: the system prompt, every message in `messages` (including tool results, images, and documents), and your tool definitions. The output Claude generates for the turn... counts too."
   - checked

5. A full window leaves no room to answer. Plan: Section 1, Nuance 2.
   - Link: https://platform.claude.com/docs/en/build-with-claude/context-windows
   - Title: Context windows
   - Support: The window "holds the conversation history plus the new output Claude generates." If generation reaches the limit, it "stops with `stop_reason: "model_context_window_exceeded"`." If input alone exceeds it, the API returns a 400 error ("prompt is too long").
   - checked

6. You pay for the tokens you send and the tokens the model writes. Plan: Section 1, Nuance 3.
   - Link: https://platform.claude.com/docs/en/build-with-claude/context-windows
   - Title: Context windows
   - Support: Thinking tokens "are billed as output tokens"; kept history "billed as input tokens, like the rest of the conversation history."
   - checked (the page shows input and output billing; it states no prices, and the lesson must not either)

7. Long or rare words take more tokens. Plan: Section 1, Nuance 1.
   - Link: https://platform.claude.com/docs/en/about-claude/glossary
   - Title: Glossary (Claude Platform Docs)
   - Support: "smaller tokens allow a model to handle uncommon or never-before-seen words"; characters per token "depends on the model and the language."
   - checked (the code and numbers part is not covered; see Gaps)

8. Code and numbers often take many tokens. Plan: Section 1, Nuance 1.
   - Not found. See Gaps.

9. Each step resends the whole history; the model keeps nothing between calls. Plan: Section 2.
   - Link: https://platform.claude.com/docs/en/build-with-claude/context-windows
   - Title: Context windows
   - Support: "Input phase: Contains all previous conversation history plus the current user message." "previous turns are preserved completely." Each response "becomes part of the input for the next turn."
   - checked

10. Tool results stay in the history and count at every later step. Plan: Section 2, Nuance 2.
    - Link: https://platform.claude.com/docs/en/build-with-claude/context-windows
    - Title: Context windows
    - Support: "every message in `messages` (including tool results...)" counts toward the window. Tool turn 2 input is "Every block in the first turn and the `tool_result`."
    - checked

11. Ways to keep it small: clear old tool results and summarize earlier steps. Plan: Section 2, Nuance 3.
    - Link: https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents
    - Title: Effective context engineering for AI agents
    - Support: "Compaction is the practice of taking a conversation nearing the context window limit, summarizing its contents." "clearing tool calls and results" is "one of the safest lightest touch forms of compaction." Warning: "overly aggressive compaction can result in the loss of subtle but critical context."
    - checked

12. Set a step limit. Plan: Section 2, Nuance 3.
    - Not found in the article or docs I opened. See Gaps.

13. The program runs the tool and returns the result to the model. Plan: Opening warm-up 2, Section 2 Nuance 1.
    - Link: https://platform.claude.com/docs/en/agents-and-tools/tool-use/memory-tool
    - Title: Memory tool
    - Support: "Claude requests file operations, and your application runs them." The application "returns the result in a `tool_result` block"; this is "the standard tool-use loop."
    - checked

14. When a session ends the context is gone; saved notes outside the context carry facts to the next session. Plan: Section 3.
    - Link: https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents
    - Title: Effective context engineering for AI agents
    - Support: "the agent regularly writes notes persisted to memory outside of the context window."
    - checked
    - Second source: https://platform.claude.com/docs/en/agents-and-tools/tool-use/memory-tool (Memory tool): "files that persist between sessions, building up knowledge over time without keeping everything in the context window." Its prompt text says "Your context window might be reset at any moment."
    - checked

15. Notes can be written by the model through a tool, and the program stores them. Plan: Section 3.
    - Link: https://platform.claude.com/docs/en/agents-and-tools/tool-use/memory-tool
    - Title: Memory tool
    - Support: "The memory tool operates client-side"; "Memory lives entirely in your application"; the handler maps `/memories` onto "a per-user directory or keys in a database."
    - checked

16. Save only lasting facts; notes can go stale and need pruning. Plan: Section 3, Nuances 1 and 2.
    - Link: https://platform.claude.com/docs/en/agents-and-tools/tool-use/memory-tool
    - Title: Memory tool
    - Support: "Memory expiration: Periodically delete memory files that haven't been accessed in a long time." "Track memory file sizes and cap how large a file can grow." "Only write down information relevant to <topic> in your memory system."
    - checked (it supports pruning and limits; the "store the date" and "staff correct a record" advice is design advice)

17. Training status should sit in the program's own database that the program checks, not only in the model. Plan: Section 3, Nuance 3.
    - A design choice that the plan says to state in plain words. No source found. See Gaps.

18. Manuals too long for the window are handled by retrieval (RAG). Plan: Section 4.
    - Link: https://www.anthropic.com/news/contextual-retrieval
    - Title: Contextual Retrieval (Anthropic)
    - Support: "For larger knowledge bases that don't fit within the context window, RAG is the typical solution."
    - checked
    - Also the glossary (https://platform.claude.com/docs/en/about-claude/glossary): RAG passes "an external knowledge base or a set of documents... into the context window"; "relevant information first must be retrieved from the knowledge base based on the input prompt, and then passed to the model along with the original query."
    - checked

19. Only the best few chunks go into the context. Plan: Section 4, example.
    - Link: https://www.anthropic.com/news/contextual-retrieval
    - Title: Contextual Retrieval
    - Support: "Pass the top-K chunks into the model as context to generate the final result."
    - checked

20. Search by keywords versus search by meaning (embeddings). Plan: Section 4.
    - Link: https://www.anthropic.com/news/contextual-retrieval
    - Title: Contextual Retrieval
    - Support: "While embedding models excel at capturing semantic relationships, they can miss crucial exact matches." BM25 "is particularly effective for queries that include unique identifiers or technical terms."
    - checked

21. A chunk can lose its meaning when cut out; adding context to each chunk helps. Plan: Section 4, Nuance 2.
    - Link: https://www.anthropic.com/news/contextual-retrieval
    - Title: Contextual Retrieval
    - Support: A chunk "on its own doesn't specify which company it's referring to or the relevant time period"; "Contextual Retrieval solves this problem by prepending chunk-specific explanatory context to each chunk before embedding."
    - checked

22. Retrieval can be a tool so the model decides when and what to search. Plan: Section 4, Nuance 3.
    - Link: https://platform.claude.com/docs/en/about-claude/glossary
    - Title: Glossary (Claude Platform Docs), RAG entry
    - Support: "the model itself does not necessarily retrieve the data (but can with tool use and a retrieval function)."
    - checked
    - Also the article (https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents): just-in-time agents "dynamically load data into context at runtime using tools."
    - checked

23. Retrieval can return the wrong thing, so test it. Plan: Section 4, Nuance 1.
    - Link: https://platform.claude.com/docs/en/about-claude/glossary
    - Title: Glossary (Claude Platform Docs), RAG entry
    - Support: "the effectiveness of RAG depends on the quality and relevance of the external knowledge base and the knowledge that is retrieved at runtime."
    - checked (the advice to test real questions is the writer's own)

24. Long contexts make the model less precise; a bigger window does not mean send everything. Plan: Misconception 2.
    - Link: https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents
    - Title: Effective context engineering for AI agents
    - Support: "as the number of tokens in the context window increases, the model's ability to accurately recall information from that context decreases." "Context, therefore, must be treated as a finite resource with diminishing marginal returns."
    - checked
    - Also https://platform.claude.com/docs/en/build-with-claude/context-windows (Context windows): "more context isn't automatically better. As token count grows, accuracy and recall degrade, a phenomenon known as context rot."
    - checked

25. Changing data (the booking calendar) is read with a tool when needed, not saved. Plan: Section 5, Nuance 3.
    - Link: https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents
    - Title: Effective context engineering for AI agents
    - Support: Just-in-time agents "maintain lightweight identifiers" and "dynamically load data into context at runtime using tools"; memory "supports just-in-time context retrieval" (memory tool doc).
    - checked

26. Chat apps appear to remember because the app saves and resends the text; the model does not keep it. Plan: Misconception 1.
    - Closest: the context windows doc says previous turns are resent in the API, and claude.ai "can also manage the context window on a rolling 'first in, first out' basis." It does not say what a chat app saves. See Gaps.

27. A chatbot can state an outdated fact because its knowledge stops at its training data, and it writes plausible text whether or not true. Plan: Opening warm-up 1 (record 0001).
    - Partial only: the glossary says RAG lets a model "access and use information beyond its training data." The "plausible text" part is not sourced here. See Gaps.

## Community

- Link: https://forum.langchain.com
- Title: LangChain Forum (Discourse, run by the LangChain team)
- What to ask or share: Post in "Talking Shop" (general discussion of "anything related to building agentic applications"). Share the three-decision sketch (what stays in context, what is saved as notes, what is retrieved) for the makerspace assistant and ask what breaks. For example, ask how others keep manual chunks small, or how they store per-user notes. I did not see a memory or retrieval category there, so use "Talking Shop" or "OSS Product Help".
- Caveat: The forum is tied to the LangChain framework. Mention that the learner is framework-neutral.
- checked (page opened; categories read)

## Gaps

- Claim 2: the "3/4 of a word" rule is not in a Claude page I opened. Only the glossary figure (about 3.5 characters on earlier models, about 30 percent more tokens on newer ones) is checked. The writer should say "about 3 to 4 characters, roughly three-quarters of a word, a rough rule that varies by model", or use the character figure.
- Claim 8: no source for "code and numbers often take many tokens".
- Claim 12: no source for a step limit as a way to keep context small.
- Claim 17: no source; it is a design choice that the lesson states in plain words.
- Claim 26: no opened source says what chat apps save and resend.
- Claim 27: no source for "writes plausible text whether or not true". It comes from record 0001 of the learner's earlier work.

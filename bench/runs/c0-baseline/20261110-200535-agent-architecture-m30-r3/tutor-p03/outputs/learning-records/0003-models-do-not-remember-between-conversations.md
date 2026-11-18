# A model does not remember earlier conversations; the program must store and re-supply them

Riley believed that a language model automatically remembers earlier conversations, so the makerspace assistant would remember what each student said last week. This was corrected in the chat: the model keeps nothing between calls, and any memory has to be saved by the program and put back into the input text.
This is the base for the context-and-memory work: what the assistant keeps in context, and what it saves between sessions.

**Evidence:** Riley's own question stated the misconception; the correction was given in the chat on 2026-11-10. It has not yet been checked that the correction landed.

**Implications:** Follows from record 0001 (the model knows only its training plus the text it is given). Next lesson on context and memory should start by having Riley design what the assistant saves per student and how it gets back into the input.

# Plan: Lesson for O3, context and memory in an agent

Requested length: 30 minutes. Total words: 4,500 (150 x 30). Fits the 2,700 to 6,750 range.
Lesson file to write later: `lessons/0001-context-and-memory.html` (the `lessons/` folder is empty, so the next number is 0001). Meta tags: `p3-minutes` = 30, `p3-objective` = O3.
Notes for the writer: `RESOURCES.md` does not exist yet, so create it and record every source used. There are no earlier lessons to link to. Open the three sources and check every claim before citing it. The primary source is the Anthropic context-engineering article.

## The win

By the end of this lesson Riley can decide, for the makerspace assistant, what stays in context, what is saved between sessions as notes (for example a student's training status), and how the assistant finds the right page in a long manual (retrieval).

## Numbers

- Reading time = section words / 150.
- Practice time: 0.5 minute for each multiple-choice check, 1 minute for the faded worked task.
- Quiz after the lesson: 5 items, 5 minutes.
- Learner total = 30.0 reading + 3.5 practice + 5.0 quiz = 38.5 minutes. The limit is 1.4 x 30 = 42, so no section is cut.
- The warm-up questions are part of the opening's reading time. Their answers are revealed on demand.

## Opening (300 words)

- The win in one sentence, as above, and the time (30 minutes).
- Motivation tied to the mission: the sponsor's model budget is small, the manuals are long, and students come back each week. The assistant must answer from long manuals, remember training status, and stay cheap. This lesson gives Riley the three decisions that control that.
- Warm-up, two recall questions with answers on demand:
  1. (Record 0001) Why can a chatbot state an outdated fact with confidence? Answer: its knowledge stops where its training data stops, and it writes plausible text whether or not the text is true.
  2. (Record 0002) In the agent loop, which part runs a tool, and what happens to the result? Answer: the program runs the tool, and the result goes back to the model as new text for the next step.
- A one-line bridge: tools, context and memory all come down to what the model is given as input (record 0001).
- Reading 2.0, practice 0.0, total 2.0.

## Section 1: The context window and tokens (620 words)

- One idea: the context window is the limit on how much text the model can read in one call, and it is counted in tokens. Tokens are also what you pay for.
- Terms, one at a time: token (a small piece of text, often a word or part of a word; about 3/4 of an English word, as a rough rule); context window (all the tokens the model can see in one call, including its own reply). Define each where it first appears.
- Words 620. Reading 4.1, practice 0.5, total 4.6.
- Example: the makerspace assistant gets the question "How do I change the blade on the band saw?" The call holds: instructions (about 300 tokens), tool descriptions, the question, the manual page that answers it (about 700 tokens), and the answer. Show a simple count with round, labeled illustrative numbers. Do not state real prices.
- Analogy (maps part for part): a whiteboard of fixed size in a meeting room, 40 lines. The board is the context window. One line is about one token. The model reads the whole board before it writes each answer; its own answer also takes lines. Where it stops: the board has no cost per line, but tokens do, and the model does not "look at" lines like a person does.
- Nuances after the example:
  - Nuance 1: Tokens are not words. Long or rare words take more tokens, and code and numbers often take many.
  - Nuance 2: The window holds the input and the reply together, so a full window leaves no room to answer.
  - Nuance 3: You pay for the tokens you send and the tokens the model writes, so a short context costs less (cost per request, from `MISSION.md`).
- Figure 1: a horizontal bar for one window, split into labeled parts (instructions, tools, question, manual page, reply, free space). It shows that everything shares one limit.
- Practice check (MCQ, correct option b): a question about what the context window limits. Example stem: the assistant call has the instructions, the manual and the question; what is the window limit counted on? Options of equal length; option a (words in the question only), c (pages the program can store), d (number of tools it can call) are tempting wrong answers.

## Section 2: Each step resends everything (600 words)

- One idea: a model call keeps nothing from the call before. At every step of the agent loop, the program sends the whole history again, so the context grows and the cost of each step grows.
- Term: stateless (the model keeps nothing between calls; the program supplies all of it).
- Words 600. Reading 4.0, practice 0.5, total 4.5.
- Example: the request "Is the laser cutter free on Friday, and book me 2 pm?" in three steps. Step 1 sends the question (about 400 tokens with instructions). Step 2 sends the question, the calendar tool call and the calendar result (about 900). Step 3 sends all of that plus the booking call and result (about 1,300). Total tokens sent: about 2,600, not 1,300. Use round numbers and label them as illustrations.
- Analogy: a helper with total amnesia who gets the whole printed transcript handed over before each reply. Helper = model. Transcript = the context the program resends. Handing it over = one model call. Where it stops: a human would find it tiring to re-read it; the model has no such limit except the window and the cost.
- Nuances after the example:
  - Nuance 1: The program keeps the history, not the model. Records 0002: the program runs each tool, and each step is a separate model call.
  - Nuance 2: Long tool results stay in the history for every later step. A 5,000-token manual page costs you again at each step.
  - Nuance 3: Ways to keep it small: trim old tool results, summarize earlier steps, and set a step limit (point to the source on context engineering for these).
- Figure 2: three stacked bars for step 1, step 2 and step 3, each taller than the one before, with the new part of each bar in the accent color. It shows growth and repeat sending.
- Practice check (MCQ, correct option d): the assistant takes 4 steps; what is true about the tokens sent at step 4? Wrong options: only the newest result is sent; the model recalls earlier steps itself; the cost is the same as at step 1. Equal length.

## Section 3: Between sessions, notes are memory (600 words)

- One idea: when a session ends, the context is gone. The assistant remembers a student only if the program saves facts, for example in a notes file or a database, and loads them at the next session.
- Terms: session (one conversation from start to end); memory (facts the program saves outside the context and loads back in). Define notes as a small saved record, written by the program or by the model through a tool.
- Words 600. Reading 4.0, practice 0.5, total 4.5.
- Example: Dana finished laser cutter training on Monday. On Thursday she opens a new chat. Without saved notes, the assistant does not know she was trained. With a notes record (`{"student": "dana", "trained": ["laser cutter"], "date": "Mon"}`), the program loads it at the start and puts one line into the context. Show a short Python-flavored fragment (read JSON, build the line), since Riley knows Python and JSON.
- Analogy: a shop whiteboard that is wiped each night, plus a paper folder per student in a cabinet. Whiteboard = context; wipe = session end; folder = notes file; taking the folder out in the morning = the program loading notes. Where it stops: a person can choose to read a folder; the model reads only what the program puts in the context.
- Nuances after the example:
  - Nuance 1: Save only facts that last (training status, preferences); do not save the whole chat, because loading it costs tokens at every session.
  - Nuance 2: Saved notes can be wrong or old. Store the date, and let a staff member correct a record.
  - Nuance 3: Training status decides who may use a machine, so keep it in the program's own database that the program checks. The model may read it but must not be the only guard. This is a design choice, said in plain words.
- Figure 3: a two-lane timeline, Monday session and Thursday session, with the context erased between them and a notes file linking them. It shows what survives.
- Practice check (MCQ, correct option a): what does the assistant need to know that Dana was trained on Monday? Wrong options: the model stored it in training; the window keeps old chats; the web chat tool remembers it. Equal length.

## Section 4: Retrieval finds the right page (650 words)

- One idea: the manuals are too long for the window and too costly to send each step. Retrieval splits them into small pieces, searches the pieces for the user's question, and puts only the best few into the context.
- Terms, one at a time: chunk (a small piece of a document, for example one section or a few paragraphs); retrieval (searching the chunks and bringing back the best ones); index (the prepared list that makes the search fast). Mention search by keywords and search by meaning (embedding) in one plain sentence each, without the math (math is out of scope in `MISSION.md`).
- Words 650. Reading 4.3, practice 0.5, total 4.8.
- Example: the band saw manual has 120 pages (about 60,000 tokens). Step 1: split it into 240 chunks of about 250 tokens, each tagged with the machine and section. Step 2: the student asks "How do I change the blade?" Step 3: the search returns the top 3 chunks (about 750 tokens). Step 4: only those 3 chunks go into the context. Compare: 750 tokens versus 60,000 tokens at every step.
- Analogy: the index at the back of a book. Index entry = search index; page number = chunk; reading only the pages named = putting only the best chunks in context. Where it stops: a book index uses exact words; retrieval by meaning can match "change the blade" with "replace the saw band".
- Nuances after the example:
  - Nuance 1: Retrieval can return the wrong chunk, so the answer can be wrong. Check by testing real questions.
  - Nuance 2: A chunk can lose its meaning when cut out ("Remove the guard" - which machine?). Adding the machine name and section to each chunk helps; the contextual retrieval source covers this.
  - Nuance 3: The retrieval can be a tool in the agent loop, so the model decides when to search and with which words.
- Figure 4: a left-to-right pipeline: manual, chunks, index, search with the question, top 3 chunks, context window. It shows that only a small part reaches the model.
- Practice check (MCQ, correct option c): why does the assistant search chunks instead of sending the whole manual at each step? Wrong options: the model cannot read PDF files; the manual would be lost after each session; chunks are always more exact than pages. Equal length.

## Section 5: Deciding what goes where (450 words)

- One idea: each piece of information has one best place: in the context now, in saved notes, or in a searchable store. Ask three questions: Is it needed at every step? Does it last past this session? Is it too long to carry?
- Words 450. Reading 3.0, practice 0.5, total 3.5.
- Example: a decision table for the assistant with four rows: the assistant's rules (in context, every step); the student's question and the tool results of this request (in context, trimmed after use); training status (saved notes, loaded at session start); machine manuals (searchable store, only the best chunks). Each row has the answer to the three questions.
- Nuances after the example:
  - Nuance 1: Information can move: a retrieved chunk is in context for one request, then leaves.
  - Nuance 2: Every item in context costs tokens at every step, so ask what can leave.
  - Nuance 3: The booking calendar changes all the time, so it is read with a tool when needed. It is not saved as a note.
- Figure: none. The table is enough (use a table, per `LESSONS.md`).
- Practice check (MCQ, correct option b): a new item, for example "the student's favorite machine" or "the opening hours that change each term"; where does it go? Equal-length options; the answer needs the three questions, so the learner applies them to a new case.

## Misconceptions (300 words)

Name each, say why it is tempting, and show with a short example why it is wrong. Put each in the misconception color. No practice check; the section sits after Section 5 so Riley can see each one with the full picture.

1. M3, memory of earlier conversations is automatic. Tempting because a chat app seems to remember. Wrong: the app saves and resends the text; the model does not keep it. Use the Dana example.
2. No id yet: "A bigger window means I can send everything." Tempting because the manual might fit. Wrong: cost grows with every step, and long contexts can make the model less precise (cite the context-engineering source after checking the exact claim).
3. No id yet: "Within one request, the model remembers earlier steps by itself." Wrong: the program resends them (Section 2).
4. No id yet: "A token is a word." Wrong: Section 1, Nuance 1.

Suggest to the tutor: give misconceptions 2 to 4 ids (M4 to M6) in `NOTES.md` after the lesson, so the quiz keys can use them.

Reading 2.0, practice 0.0, total 2.0.

## Worked example, then practice task with faded steps (700 words)

- Words 700. Reading 4.7, practice 1.0, total 5.7.
- Worked example (about 400 words), every step uses one scenario: Dana, trained on the laser cutter, writes "Can I cut 6 mm acrylic, and what are the power settings?" Steps: (1) load notes: trained on laser cutter, put one line in context; (2) retrieve: search the laser cutter manual chunks for "acrylic 6 mm power", take the top 3 chunks; (3) build the context: rules, notes line, question, 3 chunks (give token counts, about 1,800); (4) the model answers and may call the booking tool; (5) after the session, save new facts only ("asked about acrylic") if useful, and drop the chunks. Show the decision at each step with the three questions.
- Practice task, steps faded (about 300 words): a new case, Marco asks about the 3D printer: "What filament do I use, and am I cleared for the printer?" Step 1 is given in full (load notes). Step 2 is half given (what to search for). Steps 3 to 5 are blank: the learner lists what goes in the context, what is retrieved, and what is saved. The solution is on demand. Count the task as 1 minute.

## Summary and Go further (280 words)

- Words 280. Reading 1.9, practice 0.0, total 1.9.
- Summary in 4 lines: (1) the window limits what the model sees, in tokens, and tokens are cost; (2) each step resends the history; (3) between sessions only saved notes remain; (4) retrieval brings the best chunks, and the three questions decide where information goes.
- A prompt: explain in your own words, in two sentences, what the assistant keeps in context, what it saves, and how it finds a manual page.
- Go further: primary source, "Effective context engineering for AI agents" (https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents). Other sources cited: the context windows documentation (https://platform.claude.com/docs/en/build-with-claude/context-windows) and "Contextual retrieval" (https://www.anthropic.com/news/contextual-retrieval). One community where Riley can test the skill; the writer picks one after a search (do not type a URL from memory).
- The page ends after "Go further". No mention of the quiz or of chat questions; those go in the chat message.

## The table

| Part | Words | Reading min | Practice min | Total min |
|---|---|---|---|---|
| Opening and warm-up | 300 | 2.0 | 0.0 | 2.0 |
| Section 1: context window and tokens | 620 | 4.1 | 0.5 | 4.6 |
| Section 2: each step resends everything | 600 | 4.0 | 0.5 | 4.5 |
| Section 3: notes between sessions | 600 | 4.0 | 0.5 | 4.5 |
| Section 4: retrieval | 650 | 4.3 | 0.5 | 4.8 |
| Section 5: deciding what goes where | 450 | 3.0 | 0.5 | 3.5 |
| Misconceptions | 300 | 2.0 | 0.0 | 2.0 |
| Worked example and faded task | 700 | 4.7 | 1.0 | 5.7 |
| Summary and Go further | 280 | 1.9 | 0.0 | 1.9 |
| Quiz after the lesson (5 items) | 0 | 0.0 | 5.0 | 5.0 |
| Totals | 4,500 | 30.0 | 8.5 | 38.5 |

The total for the learner is 38.5 minutes against 30 requested (ratio 1.28, under the 1.4 limit). The sum of section words is 4,500.

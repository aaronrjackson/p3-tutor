# Open misconception: the model runs the tools itself (M4)

In quiz 0001, submission s1, Riley chose that the model opens the booking system itself (q2) and counted 1 model call because "it runs the 3 tools itself" (q4). In reality the model only writes a tool request, the program runs the tool, and each request or answer is one model call.
Riley also wrote that the model remembers earlier sessions on its own (q6, M3). This matters for the next topic, context and memory.

**Evidence:** quiz 0001, submission s1, items q2, q4 and q6. Riley got q1 (the loop) and q3 (step limit) right.

**Implications:** Before teaching context and memory, fix M4 with a step-by-step trace that labels each step "model call" or "program runs tool". Teach M3 directly: the model only sees its current input, so memory between sessions is something the program must build. Submission s2 may show whether this has changed.

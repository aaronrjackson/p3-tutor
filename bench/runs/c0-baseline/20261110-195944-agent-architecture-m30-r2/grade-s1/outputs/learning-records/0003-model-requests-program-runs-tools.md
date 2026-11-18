# Open misconception: the model runs the tools itself (M4), and remembers between sessions (M3)

On quiz 0001 (s1), Riley chose that the model opens the booking system itself (q2) and said it "runs the 3 tools itself" in one call (q4). In q6 they added that the model remembers earlier sessions on its own. Riley does know that the model gets tool descriptions and picks the one that fits, and that a step limit stops a stuck loop.

**Evidence:** quiz 0001, submission s1, items q2, q4, q6 (wrong or partial), q1 and q3 correct.

**Implications:** Before building on the loop, re-teach the split: the model only writes a tool request, and the program runs the tool, adds the result to the next input and calls the model again, so each step is a separate model call. The context and memory lesson should start by showing that the model keeps nothing between calls unless the program supplies it. Check whether submission s2 (taken later, from memory) shows this fixed.

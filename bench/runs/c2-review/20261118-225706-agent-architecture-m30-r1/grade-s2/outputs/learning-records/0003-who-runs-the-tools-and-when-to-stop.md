# Riley knows the loop and tool requests, but not yet who runs tools or why a loop needs a stop

On the second attempt at quiz 0001, Riley correctly identified the loop as what makes an agent (q1), saw that the model only outputs a tool request (q2), and explained that the tool result goes back as the next input (q5).
Two gaps remain. Riley still says the model "runs" each tool (M4) while counting the 4 model calls correctly (q4). Riley chose "let it run longer" for a looping agent (q3, M6), and described tool choice by name only (q6).

**Evidence:** quiz 0001, submission s2, items q1-q6. In s1, Riley chose "a" on q2 (M4), so q2 improved.

**Implications:** Re-teach that the program runs tools and each result starts a new model call. Teach stopping conditions (step limits) before multi-step design. Tool descriptions (name, purpose, parameters) are the next topic that connects to the mission goal of writing tool descriptions. Submission s1 is still ungraded.

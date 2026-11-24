# Reviews: c3-split

Your quick rounds while you split up the teach job, and then the major review of `c3-split`.
Add one subagent of the teach pipeline per round, so the run before it shows the lesson without it and the run after it shows the lesson with it.
The major review covers the lesson only, and its previous step is `c2-review`.
`reviews/README.md` says how to write each part.
You write your thoughts, ratings and feedback; Claude Code writes only the What changed part of each round.
Keep every heading as it is, because `p3 check` reads them, and add a round by copying the last one with its marker lines.

## Quick rounds

### Round 1

**Run:** `bench/runs/_live/20261124-194203-agent-architecture-m30-r1`

**My thoughts:**

I think some of the figures could probably be better drawn. The context window diagram I think could have the text on the right be better described / aligned with the model instead of kind of just sitting on the side. Same thing with the diagram with Manuals -> Context Window (this run only) <-> Saved notes (all session) which has the text 'search tool' and 'save_note' and 'load at start' kind of just sitting at the bottom and its not exactly clear what text relates to what on the image.

**What changed:**

- Kind: new subagent
- Files: tutor/.claude/agents/figure-designer.md, tutor/.claude/skills/teach/SKILL.md
- Why: Your thoughts found figures whose labels sat apart from the parts they name, so a figure-designer subagent now draws the lesson's figures with every label on or beside its part, and the teach skill starts it after the lesson is written and leaves the rest of the lesson as it is.

### Round 2

**Run:** `bench/runs/_live/20261124-195655-agent-architecture-m30-r1`

**My thoughts:**

The diagrams look much better now. Labels line up clearly with arrows or specific parts of the diagram. Much less unambiguous. Overall, it looks really good. However, at the end, it says:

"Anything unclear? Ask me in the chat; I can explain any part again, another way, or go deeper.

A short quiz on this lesson is ready (quiz 0002): ask me for it when you want to check what stuck."

However, this is a website/HTML file that's being generated. It's not a chat window that you're speaking to. In my opinion at least, I think it just reads better with those removed.

**What changed:**

- Kind: modified skill
- Files: tutor/.claude/skills/teach/references/lesson-template.html, tutor/.claude/skills/teach/references/LESSONS.md
- Why: Your thoughts said the closing lines about asking in the chat and the ready quiz do not belong on a web page, so the lesson template and guide no longer end with them, and the tutor says those things in its chat message instead.

### Round 3

**Run:** `bench/runs/_live/20261124-201451-agent-architecture-m30-r1`

**My thoughts:**

My thoughts from the previous round were addressed and look good now. I want to add one subagent: A planner subagent, that will make a plan with a word budget for section and also create an accurate reading of how long it'll take for someone to read through each section and do the associated quiz. The second is a references subagent, which reads the plan's claims and finds high-trust resources, each one checked, for the lesson to cite.

**What changed:**

- Kind: new subagent
- Files: tutor/.claude/agents/planner.md, tutor/.claude/skills/teach/SKILL.md
- Why: Your thoughts asked for a planner that sets a word budget for each section and the time to read it and do its practice, so a planner subagent now writes that plan to drafts/plan.md and the teach skill starts it and writes the lesson to the plan in the style you approved.

### Round 4

**Run:** `bench/runs/_live/20261124-202814-agent-architecture-m30-r1`

**My thoughts:**

The lesson looks and feels balanced, and the pacing feels right. The estimates of reading time is more or less accurate. I want to add one more subagent: A references subagent, which reads the plan's claims and finds high-trust resources, each one checked, for the lesson to cite.

**What changed:**

- Kind: new subagent
- Files: tutor/.claude/agents/references-finder.md, tutor/.claude/skills/teach/SKILL.md
- Why: Your thoughts asked for a references subagent that reads the plan's claims and finds checked high-trust sources, so a references-finder subagent now writes them to drafts/sources.md and the teach skill starts it and cites only from that list, keeping the lesson's style.

## Major review

**Run:** `bench/runs/c3-split/20261124-204102-agent-architecture-m30-r1`

**Live tries:**

.

### Lesson

#### Technical correctness and facts

Rating: 5/5

#### Pedagogy

Rating: 5/5

#### Alignment with the learning goal

Rating: 5/5

#### Overall quality

Rating: 5/5

### Compared with the previous step

Nearly identical

### What the next step should fix

I do not believe there is much that needs to be or should be fixed. I am quite happy with this current iteration. The main thing, non-content wise, is the time to run this took far longer and cost more than c2-review (19.5 minutes and cost $1.76, vs only 2.8 minutes and cost $0.71 for c2-review). This lesson did not improve enough to justify costing more than double and also taking more than 6 times longer to run. Something I think that works really well that was added here was the time estimation at the start of each header (e.g. The context window and tokens 5 min), as I think it keeps the reader a little more engaged when they first see the wall of text of a lesson.
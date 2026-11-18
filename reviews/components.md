# Components

One entry for every skill and every subagent you built, from `c1-skills` to `final`, including the ones you dropped, even one you took out again before any snapshot.
The heading is the skill's folder name or the subagent's `name` from its frontmatter, and `reviews/README.md` says what each field holds.
Replace the empty entry at the bottom with your first component, and copy it for each one after that.
Claude Code may fill in Kind, Step added, and With and without; Purpose, Review and Kept in final are yours.

<!--
An example of a finished entry:

### quiz-reviewer

- Kind: subagent
- Step added: c2-review
- Purpose: My c1 review found two quiz items that could be read two ways (q2 and q4) and one whose correct option repeated the stem; a reviewer with a fresh context reads the draft the way a learner will, which the quiz skill writing its own items cannot do, so it is a subagent and not a step in the skill.
- With and without: reviews/c2-review.md, Round 1 (without) and Round 2 (with)
- Review: Without it, q2 asked which design "is better" with no criterion; with it, every stem names its criterion and the reviewer's record shows two items flagged and fixed in one pass, for about 0.6M more tokens per quiz, which I think a quiz is worth, because a misread item teaches the wrong thing.
- Kept in final: yes
-->

### teach

- Kind: skill
- Step added: c1-skills
- Purpose: The tutor needs this skill to best understand how to best teach a lesson to a user in a style that they understand and agree with. It is a skill because the user is interacting with one agent, and this agent needs all the context that a subagent wouldn't have.
- With and without: reviews/c1-skills.md, Round 1 (without) and Round 2 (with)
- Review: It's good. The mid-lesson quizzes are really effective at retention, analogies are clear and understandable, explanations are short and concise, nuance is clear and unambiguous. The main difference is the original output was maybe more verbose or ambiguous with its wording.
- Kept in final: TODO

### tutor

- Kind: skill
- Step added: c1-skills
- Purpose: The tutor needs this skill to best understand how to answer the questions a student has about a topic concisely. It is a skill because the user is interacting with one agent, and this agent needs all the context that a subagent wouldn't have.
- With and without: reviews/c1-skills.md, Round 4 (without) and Round 5 (with)
- Review: The replies used to run ~220+ words, against a limit of 200. This was a failure. The new output fixes this, and seemingly reliably will now reply in <200 words. As well, it now never specifically mentions 
- Kept in final: TODO

### quiz

- Kind: skill
- Step added: c1-skills
- Purpose: The tutor needs this skill to best understand how to produce a quiz that is useful and understandable for the user. It is a skill because the user is interacting with one agent, and this agent needs all the context that a subagent wouldn't have.
- With and without: reviews/c1-skills.md, Round 5 (without) and Round 6 (with)
- Review: Quizzes now offer shorter questions that are more concise and unambiguous to understand.
- Kept in final: TODO

### grade

- Kind: skill
- Step added: c1-skills
- Purpose: The tutor needs this skill to best understand how to grade a user's quiz and offer feedback that expresses what they did right or did wrong. It is a skill because the user is interacting with one agent, and this agent needs all the context that a subagent wouldn't have.
- With and without: reviews/c1-skills.md, Round 6 (without) and the major review (with)
- Review: Pretty much unchanged.
- Kept in final: TODO

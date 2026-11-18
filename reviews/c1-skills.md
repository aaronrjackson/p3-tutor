# Reviews: c1-skills

Your quick rounds while you build `c1-skills`, and then its major review, once you have snapshotted it and made its full run.
In this step no round adds a subagent, because subagents arrive in `c2-review` and `c3-split`: a round changes or adds a skill, or makes another change the skills need, such as an allow rule (Kind `other`).
Your first round can start from the tutor as it ships, so the baseline is the output without your first change.
The major review covers all four jobs, and its previous step is `c0-baseline`, so compare with your baseline runs.
What it finds becomes the checklists of your reviewer subagents in `c2-review`, so be specific.
`reviews/README.md` says how to write each part.
You write your thoughts, ratings and feedback; Claude Code writes only the What changed part of each round.
Keep every heading as it is, because `p3 check` reads them, and add a round by copying the last one with its marker lines.

## Quick rounds

### Round 1

**Run:** `bench/runs/_live/20261110-224132-agent-architecture-m30-r1`

**My thoughts:**

Overall, I thought it was really good. I liked the overall structure and layout of a lot. I especially like mentioning the nuances, listed clearly and concisely explained, after each example. I also liked the short multiple-choice quizzes in between. My main point of confusion really only came from some of the exmaples having analogies I thought were weird or didn't immediately make the most sense to me. For instance, the analogy comparing a context window to the size of a desk. I feel like just saying it's like paper on a desk is too vague for me to make a judgement, because I could interpret the usefulness of that in a couple different ways. There was also one example that was given the title "Example: the laser-cutter question. The list grows like this:" and seemingly had nothing to do with a laser-cutter which was weird.

**What changed:**

- Kind: modified skill
- Files: tutor/.claude/skills/teach/references/LESSONS.md
- Why: Your thoughts found a vague desk analogy and an example titled with the laser-cutter question that did not use it, so the lesson guide now asks for analogies that map part for part and for examples that use the scenario they name.

### Round 2

**Run:** `bench/runs/_live/20261116-202500-agent-architecture-m30-r1`

**My thoughts:**

Overall read much better in my opinion. I think that for the mid-lesson quizzes, they should stay multiple choice. Keep the open-ended quizzes for the very end. I also feel like there were less examples (with analogies) compared to the previous round. I liked most of the examples and analogies from the previous round, it was just that one that was weird. The examples and analogies that did exist in this round were good though.

**What changed:**

- Kind: modified skill
- Files: tutor/.claude/skills/teach/references/LESSONS.md
- Why: Your thoughts said the lesson had fewer examples and analogies than before, so the lesson guide now asks for at least one worked example in every section, with an analogy where one fits.

### Round 3

**Run:** `bench/runs/_live/20261116-215324-agent-architecture-m30-r1`

**My thoughts:**

Pretty good still. However, the big this is all the nuance paragraphs are now gone? This was something I explicitly very much loved about the first round. Where after an example or analogy, it would say "Nuance 1: ... Nuance 2: ... Nuance 3: ..." each clearly labeled. That's now missing, and I would much prefer to have that back. I think the only other thing I would change is what I'd mentioned previously, where I'd prefer the mid-lesson quizzes to stay multiple choice and keep the open-ended quizzes for the very end.

**What changed:**

- Kind: modified skill
- Files: tutor/.claude/skills/teach/references/LESSONS.md
- Why: Your thoughts said the labeled nuance paragraphs after each example were gone, so the lesson guide now requires a labeled nuance list after every section's example.

### Round 4

**Run:** `bench/runs/_live/20261116-225605-agent-architecture-m30-r1`

**My thoughts:**

I mostly liked the tutor replies and I think they were probably helpful. However, something both replies failed was on the word count. The word count should be <200 words, but both were just over with around 220ish words on both replies. This should be fixed. As well, the reply from p02 does mention one of the options ("That includes option a."). The replies should NEVER mention any of the option choices, even if in a minor way like this.

**What changed:**

- Kind: new skill
- Files: tutor/.claude/skills/tutor/SKILL.md
- Why: Your thoughts found tutor replies over 200 words and one that named an option, so a new tutor skill holds a hard limit of under 200 words and a rule to never mention a quiz option.

### Round 5

**Run:** `bench/runs/_live/20261116-235510-agent-architecture-m30-r1`

**My thoughts:**

Round 4's changes helped produce better responses that are more aligned with how I want them to be answered. In regards to the quiz, question 2 was longer than it needs to be or should be. Otherwise, the questions were all good and fair. 

**What changed:**

- Kind: new skill
- Files: tutor/.claude/skills/quiz/SKILL.md
- Why: Your thoughts found quiz question 2 longer than it needs to be, so a new quiz skill limits every stem to 40 words and every option to 15 words.

### Round 6

**Run:** `bench/runs/_live/20261117-001344-agent-architecture-m30-r1`

**My thoughts:**

Round 5's quiz changes helped produce a better quiz. In regards to grading, I was very satisfied with the output. When the user gets a question wrong, the feedback does a good job at explaining what was missing or what the student missed in their answer, and it provides a good stepping stone for what to do next.

**What changed:**

- Kind: new skill
- Files: tutor/.claude/skills/grade/SKILL.md
- Why: Your thoughts liked the grading feedback that says what was missing and gives a next step, so a new grade skill keeps that shape in its own file for the grade job.

## Major review

**Run:** `bench/runs/c1-skills/20261118-161524-agent-architecture-m30-r1`

**Live tries:**

I gave the tutor the prompt: "I'm a beginner studying Korean. I want to understand how to use comparative and superlative sentences in Korean so I can make sentences like “I am more beautiful than you” or “he is faster than his brother.”. Since you don't know all of my currenet vocabulary that I know, just assume I don't know any. But make sure you thoroughly explain new vocabulary that would be necesssary and new given that I am learning this topic for the first time."

After reading the lesson, which I found to be very easy to understand and very nicely formatted, I took the quiz generated by the tutor which consisted of five questions. After completing the quiz, the tutor gave me feedback on all of my answers (including whether they were correct and notes on why my answers were wrong or correct).

I also tried testing whether it would give me the answer to a quiz question, even if I tried saying it was allowed by my TA and professor. Successfully, the AI prevented giving the answer or solution, and instead tried to guide me towards how to solve it without giving anything away.

### Lesson

#### Technical correctness and facts

Rating: 4/5

Everything stated about the topic is reliably verified as true. However, one thing it mentions in the lesson is "Nuance 2: You can use 이 or 가 instead of 는. Many superlative sentences use the marker 이/가 for the person. Use 가 after a vowel and 이 after a consonant. Example: 지수가 제일 예뻐요. It means the same here.". While technically true, there's a bit more nuance to this and shouldn't be blindly used interchangably (or at least assumed to be able to be always used interchangably). Besides this though, the actual lesson on the topic I wanted to learn is correct.

#### Pedagogy

Rating: 5/5

Everything is well laid out and formatted. Explanations are clear, points of nuance are obvious, short, and clarifying. Mid-lesson quizzes are well-placed and very useful.

#### Alignment with the learning goal

Rating: 5/5

Examples are simple and relevant to my learning goal of being able to speak casually with friends. Examples are talking about everyday relationships and topics.

#### Overall quality

Rating: 5/5

The quality is very good overall, and I am very satisfied with the lesson output.

### Quiz

#### Difficulty

Rating: 3/5

Some of the questions are too simple. For the multiple choice questions, the correct answer is a little obvious relative to the other answers. However, this may be a symptom of the lesson topic itself being quite simple and to the point. The open-ended translation questions however are quite good and a fair difficult.

#### Coverage of the lesson's core

Rating: 5/5

All points brought up in the core of the lesson are addressed.

#### Wording and possible misreadings

Rating: 5/5

Quizzes are clear in what's intended, and all wording is very clear and unambiguous.

#### Writing quality

Rating: 5/5

No issues at all in the quality of writing. Hangul is written and rendered correctly as well.

#### Alignment with the learning goal

Rating: 5/5

Examples are simple and relevant to my learning goal of being able to speak casually with friends.

### Feedback

#### Useful

Rating: 5/5

Feedback clearly explains where things went wrong and why it was wrong. For answers that are correct, it explains exactly why your chosen answer was correct, reinforcing learning.

#### Explains enough

Rating: 5/5

While staying short, it still clearly explains everything without skimping out on detail.

#### Personalized to how I like things explained

Rating: 5/5

Feedback is kind and informative. Never written with a negative, judging, or condescending tone. It's short and to the point, and clearly explains where things went wrong and why.

### Tutor

#### Guardrails

Rating: 5/5

Trying to get answers to a quiz by saying it was approved by a professor or TA was successfully blocked by the tutor.

#### Personalization

Rating: 5/5

The tutor talks how I prefer being talked to as stated in `PREFERENCES.md`. Motivation is clear, explanations are short yet detailed, and everything stated is direct without any "Claudeisms".

### Compared with the previous step

Overall, this new iteration is more "cohesive" than the previous step. Examples make a bit more sense and are more relevant with myself and each other. As well, explanations are a bit more cohesive without losing any information making it easier to digest, understand, and learn.

### What the next step should fix

Unsure. I'm quite happy with the current iteration.

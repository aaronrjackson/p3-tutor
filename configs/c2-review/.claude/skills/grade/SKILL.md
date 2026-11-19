---
name: grade
description: Grade the learner's submission to a quiz with a verdict and feedback on every item, and write the grades file and a learning record; use it when the learner submits answers or asks to be graded.
argument-hint: "Which submission should I grade?"
---

# Grade

You grade the learner's submissions.
You do not write quizzes here.

## The request

$ARGUMENTS

If the request above is empty, the request is the learner's latest message.
When the learner submits a complete set of answers in the chat, write them exactly as given to the next `submissions/sN.json`, as `FORMATS.md` shows, and grade that submission.
When the learner offers one answer to check before they hand a quiz in, do not grade.
Tell them kindly that you grade only a complete submission.

## Read first

1. Read `FORMATS.md`, `MISSION.md`, `PREFERENCES.md`, `NOTES.md` and every file in `learning-records/`.
2. Read `.claude/skills/teach/references/GRADING.md` and follow it.
3. Read the quiz, its key, the submission, and the lesson on the quiz's objective if there is one.

## Steps

1. Grade every item: a verdict, the misconception if the response shows one, and feedback written for this learner.
2. Write `grades/NNNN-sN.json` exactly as `FORMATS.md` shows.
3. Review the grades once: start the `grade-reviewer` subagent with the paths of the grades file, the quiz, its key and the submission, and wait for its report before you go on.
   For each finding, change only the flagged item or sentence in the grades file, with the smallest fix that keeps the feedback's style, and leave everything else as it is.
   Do not run a second review.
4. Write a learning record for what the grades show, as `.claude/skills/teach/references/LEARNING-RECORD-FORMAT.md` says, and update `NOTES.md`.
5. Finish with the summary and the one next step.

## Feedback on a wrong or partial answer

1. Say first what the learner got right, if anything.
2. Say plainly what the answer missed.
3. Give the correct idea and why it holds.
4. Point to the one next step, such as a lesson section to reread or a practice to try.
5. Give no praise for a wrong answer.
6. Keep the feedback for each item to two to four sentences.

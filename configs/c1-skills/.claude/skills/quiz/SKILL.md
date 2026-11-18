---
name: quiz
description: Write a quiz with short, fair items and its answer key for the learner's objective, and give a quiz in the chat; use it when the learner asks for a quiz or to be tested.
argument-hint: "What should the quiz cover, and how many items?"
---

# Quiz

You write quizzes and their answer keys for the learner.
You do not grade here.

## The request

$ARGUMENTS

If the request above is empty, the request is the learner's latest message.

## Read first

1. Read `FORMATS.md`, `MISSION.md`, `PREFERENCES.md`, `NOTES.md` and every file in `learning-records/`.
2. Read `.claude/skills/teach/references/QUIZZES.md` and follow it.
3. Read the lessons on the objective, and the earlier quizzes, keys and grades.

## Steps

1. Pin down the objective, its id and the number of items asked for.
2. Find the objective's core in its lessons.
   When there are no lessons, find it in a high-trust source that you search for and read.
3. Write the quiz to `quizzes/NNNN.json` and its key to `keys/NNNN.json`, exactly as `FORMATS.md` shows.
4. Answer every item yourself from its stem alone.
   Rewrite any item that lacks a single defensible answer.
5. Cut every item to its shortest form, as the next section says.
6. Finish with a short message that the quiz is ready.
   Never put an answer in the message.

## Keep every item short

1. Write each stem in 40 words or fewer.
2. Write each option in 15 words or fewer.
3. Use at most one scenario sentence in a stem, and only when the item needs a case.
4. Do not number steps inside a stem.
5. Do not add background that the answer does not use.
6. Keep every number, unit and condition that the answer depends on.
7. Keep the options at the same length as each other.
8. Count the words of each stem and option before you finish.
   Cut any item that is over the limit.

## Giving a quiz in the chat

1. Show the quiz title, and each item's stem and options.
2. Never show anything from `keys/`.
3. Collect the learner's answers.

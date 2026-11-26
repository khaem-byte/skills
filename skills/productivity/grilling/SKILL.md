---
name: grilling
description: Grill the user about a plan, decision, or idea, one question card at a time, ending in a written decision record. Use when the user wants to stress-test their thinking, or uses any 'grill' trigger phrase.
---

Cross-examine the user until you reach a shared understanding. Map this as a **design tree**: every decision branches into the decisions that hang off it.

The **frontier** is every decision whose prerequisites are already settled: the questions you can ask _now_ without guessing at answers you haven't heard yet.

## Ask one question per turn

Pick the frontier question the most other decisions hang off, and ask only that one. Each settled answer reshapes the tree: recompute the frontier, then pick again.

Ask it as a **card**: one `AskUserQuestion` call holding one question.

- `header`: the decision's name in a word or two.
- `question`: the decision, with the context needed to answer it cold.
- `options`: 2–4 real alternatives, your recommended answer first with "(Recommended)" on its label, each `description` stating the trade-off that option buys.

Above the card, write one line: the question number, how many questions sit on the frontier, and why you recommend what you recommend.

Where `AskUserQuestion` is unavailable, ask the same single question in text: `❓ **Q<n>** - **<title>**: <body>` followed by `➡️ <recommended answer>`.

## Cross-examine every answer

An answer settles a decision only once it survives cross-examination. Before moving on, test it:

- **Vague** ("it depends", "something simple", "we'll see"): ask for the concrete case, the number, or the example that pins it down.
- **Contradicts a settled decision**: quote both, and make the user pick which one stands.
- **Rests on an unstated assumption**: name the assumption and ask whether it holds.
- **Picked your recommendation without a reason, on a decision that is costly to reverse**: ask what would make it the wrong choice.

Follow up with another card, or in plain text when the follow-up needs a free-form answer. State disagreement plainly, with the failure you expect, then let the user decide: the _decisions_ are theirs.

## Find facts yourself

Finding _facts_ is your job. When a frontier question needs a fact from the environment (filesystem, tools, docs), dispatch a sub-agent with a fresh context window to find it, and keep asking the questions that don't depend on it: a running exploration is an unsettled prerequisite only for the questions downstream of it.

## Finish with a decision record

The interview is done when the frontier is empty: every branch of the design tree visited, every assumption spoken aloud.

Then write the **decision record** to `grill-<topic>.md` in the working directory:

- **Decisions**: each settled decision, the chosen answer, and the user's reason in their own terms.
- **Rejected**: the alternatives turned down, and why.
- **Open risks**: assumptions the user accepted knowingly, and anything you still disagree with.

Show the user the file and ask whether it is the shared understanding. Act on the plan only after they confirm it.

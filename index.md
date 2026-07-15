# Prompt Index

The routing table. Each entry: name, what it does, and — most importantly —
when to use it. The dispatcher reads this file first and loads only the
winning prompt from `prompts/<name>.md`.

Format:

```
## <name>
**Does:** <one line>
**Use when:** <situations, signals, question-shapes this prompt is for>
```

<!-- entries below -->

## blind-spot-pass
**Does:** Surfaces the user's unknown unknowns about a codebase area or unfamiliar domain so they can prompt better.
**Use when:** The user is about to work on something they admit they don't understand — "I know nothing about X in this codebase", "I don't know what X even is but I need to do Y". Signal: expressed ignorance + upcoming task. Not for learning a concept deeply (that's the learning prompts) — this is pre-task recon.

## design-directions
**Does:** Produces one HTML page with 4 wildly different design directions to react to.
**Use when:** The user wants a UI/visual thing but has no design direction yet — "I don't know what's possible", "no visual taste", exploring look-and-feel. Not for a settled design that just needs mocking — that's `mockup-first`.

## mockup-first
**Does:** Builds a single throwaway HTML file mocking a feature with fake data before touching the real app.
**Use when:** A specific UI feature is about to be built and the user wants to react to layout before implementation. The design direction is roughly known — otherwise `design-directions`.

## intervention-brainstorm
**Does:** Searches the codebase and brainstorms 10 intervention points for a rough problem, cheapest to most ambitious.
**Use when:** The user has a fuzzy product/system problem ("users churn after onboarding") and wants options, not a plan. Signal: problem statement without a chosen solution.

## interview-me
**Does:** Has the LLM interview the user one question at a time about ambiguities, prioritizing answers that would change the architecture.
**Use when:** Starting something underspecified — the user wants to be asked rather than to specify. "Interview me", "ask me questions", vague requirements before a build.

## reimplement-reference
**Does:** Reads an existing implementation and reimplements the same semantics in the user's stack.
**Use when:** The user points at concrete code (a crate, library, file) whose *behavior* they want ported. Signal: a reference implementation exists and is named.

## implementation-plan
**Does:** Writes an HTML implementation plan front-loading the decisions the user is likely to tweak, burying mechanical refactoring.
**Use when:** Before a nontrivial build, the user wants a reviewable plan. Distinct from `intervention-brainstorm` (options) — here the direction is chosen and needs a plan.

## implementation-notes
**Does:** Instructs the agent to keep an implementation-notes.md, logging plan deviations under 'Deviations' and continuing conservatively.
**Use when:** Kicking off a long autonomous implementation run where the user won't be watching. Often stacked onto a build request.

## buy-in-doc
**Does:** Packages artifacts (prototype, spec, notes) into a single persuasion doc for stakeholders, leading with the most compelling piece.
**Use when:** The work is done and needs to be *sold* — Slack pitch, team buy-in, explainer for non-participants.

## change-quiz
**Does:** Produces an HTML report explaining a change (context, intuition, what was done) with a mandatory quiz at the bottom.
**Use when:** After a change the user didn't write themselves and wants to genuinely understand — "make sure I understand what happened here". Signal: comprehension-checking a diff/change, not reviewing it for bugs.

## ladder-of-thinkers
**Does:** Explains a concept as a role-play ladder of progressively smarter thinkers, each theory dying from one concrete flaw, ending with the true answer and a moral.
**Use when:** The user wants deep *intuition* for why the right answer is right and the tempting answers are wrong — "explain X so I really get it", counterintuitive concepts, "why isn't it just...". Not for idea history — that's `heritage-line`.

## input-output-data-flow
**Does:** States a component's input and output, then walks each transformation step by step through it.
**Use when:** Understanding a specific pipeline, function, or system's data path — "what goes in and out of X", "how does data move through X". Concrete component, not a concept.

## heritage-line
**Does:** Teaches a concept through the history of its underlying ideas — a map of thinkers, taught one stop at a time in their own world, user builds the bridge back.
**Use when:** The user wants to *learn* a concept via where its ideas came from — an interactive, multi-turn study session. Distinct from `ladder-of-thinkers` (intuition via failing theories, single-shot).

## code-path-trace
**Does:** Gives the executed lines, in order, with links, from point A to point B in a codebase.
**Use when:** "How does the code get from X to Y", tracing execution, following a request/event through the system. Wants line references, not narrative — narrative is `input-output-data-flow`.

## inverted-question
**Does:** Flips "what causes X" into "what causes the absence of X", then uses the failure causes to sharpen the original answer.
**Use when:** A causal question feels stuck or the direct answer is muddy — "what causes X", "why does X happen" where inversion would illuminate.

## answer-empirically
**Does:** Replaces theoretical debate with a track record: who tried it, what happened, who rejected it, what happened.
**Use when:** A debatable claim or practice where evidence exists — "is X actually a good idea", ideology-flavored questions. Distinct from `strongest-objection`: that stress-tests an argument; this consults reality.

## afford-not-to-learn
**Does:** Extracts the lessons from a person/school the user disagrees with that survive even if their values are rejected entirely.
**Use when:** The user mentions someone they dislike or disagree with but who is successful/influential — "I can't stand X but...", learning from adversaries.

## what-breaks-if-deleted
**Does:** Answers what would break if a given thing were deleted.
**Use when:** Assessing a component's role or safety of removal — "do we still need X", "can I remove X", understanding X via its dependents.

## tradeoff-construction
**Does:** Builds the user's own decision axes first, then maps each option's trade-offs along them, concluding with "X wins if these axes dominate" rather than a verdict.
**Use when:** Evaluating or choosing between options/tools/architectures — "should I use X or Y", "is X good". Distinct from `strongest-objection` (attacking one claim) and `answer-empirically` (consulting track records) — this structures a *decision*.


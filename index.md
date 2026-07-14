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

## reverse-engineer
**Does:** Explains a system or mechanism as if you were going to build it yourself — design decisions in builder order, naive approach vs. real approach.
**Use when:** Learning how something *works internally* — a protocol, algorithm, system, or mechanism ("how does X actually work", "explain X like I'm building it"). Not for abstract concepts with no build path — that's `first-principles`.

## first-principles
**Does:** Strips a concept to its irreducible axioms and rebuilds it, flagging smuggled assumptions and historical accidents.
**Use when:** Understanding *why a concept is the way it is* — definitions, theories, frameworks, conventions ("why is X defined this way", "what is X really"). Not for buildable systems — that's `reverse-engineer`.

## strongest-objection
**Does:** States the best good-faith objection to a claim at full strength, plus what would falsify the claim, without resolving the tension.
**Use when:** Stress-testing a claim, thesis, paper, argument, or plan — "is this right", "what am I missing", "critique this", "what would a skeptic say".

## trace-the-reference
**Does:** Traces a character, image, or scene back through the myths and older works it draws on, and what the author uses the borrowing to carry.
**Use when:** Reading literature — "who/what is this character referencing", allusions, symbols, intertextual questions. Not for factual claims in nonfiction — that's `strongest-objection` territory if critique, or plain answering.

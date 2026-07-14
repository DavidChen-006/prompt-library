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

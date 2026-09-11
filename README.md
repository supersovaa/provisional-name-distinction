# provisional-name-distinction

`provisional-name-distinction` is a ChatGPT-oriented skill for preventing assistant-invented names from being mistaken for user decisions.

## Core rule

A name invented by the assistant remains visibly provisional until the user decides to adopt it.

Every assistant-authored occurrence of such a name is written as:

```text
仮称「name」
```

Once the user adopts the name, the marker is removed and the name is used normally.
If the user rejects the name, the assistant stops using it and does not reintroduce it as a candidate, recommendation, summary item, or decided value.

## What this distinguishes

The skill keeps separate:

1. names invented by the assistant for convenience;
2. names supplied by the user but not necessarily decided;
3. names the user has actually adopted;
4. names the user has rejected or replaced.

Repeating, quoting, discussing, or comparing a provisional name does not by itself count as adoption.

## Scope

The rule can apply to skill names, feature names, filenames, commands, functions, classes, modules, labels, titles, and other identifiers introduced during a conversation.

## Installation

Place `SKILL.md` where the target skill system loads skills from, or use the repository/package according to that system's installation method.

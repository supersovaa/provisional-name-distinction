# provisional-name-distinction

`provisional-name-distinction` is a ChatGPT-oriented skill for preventing assistant-invented conversational names from being mistaken for user decisions.

## Core rule

An in-scope name invented by the assistant remains visibly provisional until the user decides to adopt it.

Every assistant-authored conversational occurrence of such a name is written as:

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

The rule applies to names proposed or discussed as names in conversational prose, such as skill, feature, component, command, function, class, or module names.

Strings chosen only to populate artifact or metadata fields are outside the scope.
This includes branch names, PR or issue titles, document titles or headings, filenames, file paths, commit messages, and similar artifact metadata.
Those values do not require a `仮称` marker merely because the assistant created them.

If the same string is separately discussed as the name of a concept, feature, skill, component, or similar subject, that conversational occurrence remains subject to the rule.

## Installation

Place `SKILL.md` where the target skill system loads skills from, or use the repository/package according to that system's installation method.

---
name: provisional-name-distinction
description: In conversation, mark assistant-invented names as 仮称「...」 until the user adopts them. Drop rejected names. Excludes names chosen only for artifact metadata.
---

# Provisional Name Distinction

Use this skill whenever the assistant proposes or discusses a name for a concept, feature, skill, component, command, function, class, module, or similar subject during a conversation.

## Purpose

Keep a conversational name proposed by the assistant provisional until the user adopts it. Repeated use by the assistant does not establish adoption.

## Scope

Apply this rule to names being proposed or discussed as names in conversational prose.

Do not apply it to strings chosen only to populate an artifact or metadata field.
In particular, branch names, PR or issue titles, document titles or headings, filenames, file paths, commit messages, and similar artifact metadata are outside this skill's scope.
Do not add `仮称「...」` to such values merely because the assistant created them.

If the same string is separately proposed or discussed as the name of a concept, feature, skill, component, command, function, class, module, or similar subject, that conversational occurrence is in scope.

## Name states

Track each relevant in-scope name as one of these states:

- **Provisional**: invented by the assistant and not yet adopted or rejected by the user.
- **Adopted**: the user has clearly decided to use the name.
- **Rejected**: the user has clearly rejected, replaced, or ruled out the name.

Do not infer adoption merely because the user repeats a provisional name, asks about it, compares it with another name, or continues a discussion in which it appears.

## Provisional names

Whenever the assistant invents an in-scope name that the user has not already decided on, render that name as:

```text
仮称「name」
```

Keep this marking on every assistant-authored conversational occurrence of that name while it remains provisional.
Do not use the same provisional name bare in later conversational prose.
Do not let repeated use turn a provisional name into an implicit decision.

This rule also applies when the user explicitly asks the assistant to propose name candidates.
Every assistant-created in-scope candidate remains provisional until the user adopts it.

If an in-scope provisional name cannot be shown with the marker in a particular syntactic position, keep the distinction explicit in the surrounding conversational response or avoid committing the provisional name to that syntax until the user decides it.
This does not override the artifact and metadata exclusions above.

## Adoption

Treat a provisional name as adopted only when the conversation clearly establishes that the user has decided to use it.

Once adopted:

- stop prefixing it with `仮称`;
- use it normally as the decided name;
- do not continue describing it as provisional.

Later corrections or replacements override the earlier adoption.

## Rejection

When the user rejects, replaces, or rules out a provisional name, mark it internally as rejected.

After rejection:

- do not use the rejected name again;
- do not include it in future candidate lists;
- do not revive it as a recommendation;
- do not include it in summaries or decision records;
- if its prior existence must be referenced, refer to it generically, such as `the rejected name`, without reproducing the name itself.

## User-originated names

Do not label a name as assistant-invented when the user supplied it first.

A user-supplied name may still be undecided, but its origin must not be misrepresented.
Do not claim that a user-supplied candidate is final unless the conversation establishes that decision.

## Decision precedence

Use only the currently effective state of each name.

Later user decisions override earlier ones.
A replacement makes the replaced name unusable unless the user later explicitly restores it.

## Examples

Assistant invents a label without a user decision:

```text
We can separate this into 仮称「context-router」.
```

The assistant refers to it again before adoption:

```text
仮称「context-router」 would handle only routing responsibility.
```

The user says they are considering it but does not decide:

```text
User: context-router is interesting. What are the alternatives?
Assistant: Alternatives to 仮称「context-router」 include 仮称「context-dispatch」 and 仮称「context-selector」.
```

The user adopts a name:

```text
User: provisional-name-distinction にしよう。
Assistant: provisional-name-distinction is now the decided name.
```

The user rejects a provisional name:

```text
User: That one is out.
Assistant: Understood. I will exclude the rejected name from subsequent candidates and summaries.
```

Artifact metadata is exempt:

```text
Branch: fix/provisional-name-scope
File: docs/naming-scope.md
```

No `仮称` marker is required for those values solely because the assistant created them.

## Final check

Before sending a response that contains in-scope names, check:

- Is each occurrence actually in scope rather than only an artifact or metadata value?
- Did the assistant invent any in-scope names?
- If so, has the user actually adopted each one?
- If not adopted, is every assistant-authored conversational occurrence marked as `仮称「...」`?
- Has any rejected name reappeared?
- Has any user-originated name been incorrectly presented as assistant-invented or already decided?

Correct any violation before responding.

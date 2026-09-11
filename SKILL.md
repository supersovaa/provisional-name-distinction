---
name: provisional-name-distinction
description: Distinguish names invented by the assistant from names decided by the user. Mark every assistant-created provisional name as 仮称「...」 until the user adopts it, and stop using names the user rejects.
---

# Provisional Name Distinction

Use this skill whenever the assistant introduces or discusses names, labels, identifiers, titles, filenames, command names, function names, class names, module names, skill names, or similar user-facing identifiers during a conversation.

## Purpose

Keep assistant-invented names clearly distinct from names the user has actually decided to use.

A name invented by the assistant must never become an apparent decision merely because the assistant started using it.

## Name states

Track each relevant name as one of these states:

- **Provisional**: invented by the assistant and not yet adopted or rejected by the user.
- **Adopted**: the user has clearly decided to use the name.
- **Rejected**: the user has clearly rejected, replaced, or ruled out the name.

Do not infer adoption merely because the user repeats a provisional name, asks about it, compares it with another name, or continues a discussion in which it appears.

## Provisional names

Whenever the assistant invents a name that the user has not already decided on, render that name as:

```text
仮称「name」
```

Keep this marking on every assistant-authored occurrence of that name while it remains provisional.
Do not use the same provisional name bare in later turns.
Do not let repeated use turn a provisional name into an implicit decision.

This rule also applies when the user explicitly asks the assistant to propose name candidates.
Every assistant-created candidate remains provisional until the user adopts it.

If a provisional name cannot be shown with the marker in a particular syntactic position, do not silently present it as settled there.
Keep the distinction explicit in the surrounding response or avoid committing the provisional name to that syntax until the user decides it.

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

## Final check

Before sending a response that contains names or identifiers, check:

- Did the assistant invent any of them?
- If so, has the user actually adopted each one?
- If not adopted, is every assistant-authored occurrence marked as `仮称「...」`?
- Has any rejected name reappeared?
- Has any user-originated name been incorrectly presented as assistant-invented or already decided?

Correct any violation before responding.

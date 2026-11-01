---
name: "Writing Good Code"
description: "Important notes on writing good, succinct code, with the big picture in mind."
---

## Intro

When writing code, it's imperative to keep in mind the bigger picture.
This means writing code with *longevity*, a.k.a. "future-proof" code.
An important concept is that features almost always grow both "vertically" and "laterally".

Further, new features should also take stock of not only the *state* but the *spirit* of existing code.
A feature almost never exists in isolation, and it's important to think "how can this integrate in the best way with what is currently in place".
Of course, good practice also means refactoring existing for the new intention.

Finally, housekeeping and maintenance of existing pieces during an upgrade should not be neglected.

## Writing Generically for lateral and vertical growth

Good code has a solid foundation.
This means writing generically to plan for the future.
Often, consider if a feature deserves **base classes**, and it often will.

### No blinders--Keep your head up

It's imperative to not wear blinders while coding.
Don't get tunnel-vision on the task, **always consider the big picture**.

## Understand the repo

To write good, future-proof code, requires a **deep understanding of the repo and its direction**.

- Consult the repos `docs/` for general and specific relevant information

### Discuss with the user before making big decisions

Discussing with the user can help orient you better before making big moves.
Also, don't be shy and be transparent about your ideas.

## Less is More

Good code is succinct.
Language models and agents have a tendency to be quite verbose.
Sometimes **less is more**:

- A sprawling codebase is corrosive and linearly makes things less manageable, especially when collaborating.
- Check your **eagerness to write additive code**.
- Ask yourself:
  - "Do I really need to write ten different functions here?"
  - "Is there a better way to do this with e.g. a **base class**?"
  - "Is this **overlapping with existing functionality**? And if so, should I instead just refactor or optimize what exists?"
  - "Can this be achieved with some smart **refactoring**?"
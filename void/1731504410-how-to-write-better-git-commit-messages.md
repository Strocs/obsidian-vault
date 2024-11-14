---
id: 1731504410-how-to-write-better-git-commit-messages
aliases:
  - How to write better git commit messages
tags:
  - article
  - notes
---

# How to write better git commit messages

Based on this article: [How to write better git commit messages](https://www.freecodecamp.org/news/how-to-write-better-git-commit-messages/)

### Why? 
- Using `git log` command, we can see clearly what changes have been made.
- With a clear message, we can back to the pass to some point that we ensure have the change that are we looking for.
- Collaboration and communication

### Steps to write a better commit message
- Capitalize only the first letter, write all rest on lowercase and never end in punctuation.
- Use imperative mood, like we are giving an order or request. `Add fix for dark mode toggle state`
- Specify the type of commit, using prefixes like `Add`, `Fix`, `Update`, `Refactor`, etc.
- Length must be no longer than 50 characters.
- Be direct and avoid use of filler phrases.

### Find inner journalist

Concentrate on this questions:
- **Why** have I made these changes?
- **What** effect have my changes made? 
- **Why** was the change needed? 
- **What** are the changes in reference to? 

❌ `git commit -m 'Add margin'`
✅ `git commit -m 'Add margin to nav items to prevent them from overlapping the logo'`

In the case above, we are passing from a general commit message, that not give us any information of why, and jsut give us a vague what, to a specific one
that tell us what change are made `add margin`, where, `to nav items`, why, `to prevent them from overlapping the logo`.

### Conventional Commits




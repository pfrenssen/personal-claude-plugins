---
name: issue-posts
description: Writes issue summaries, and issue and merge request comments, in Pieter's voice. Use when drafting or rewriting an issue summary, comment, review or reply that is posted under Pieter's name, such as on drupal.org.
---

# Write an issue summary or comment in Pieter's voice

The **voice** is a colleague talking to colleagues in the issue queue: first
person, friendly, thinking out loud. It lives in Pieter's own posts in
[`examples.md`](examples.md), and the post imitates them. The voice decides how
things are said. The facts stay exactly as they are.

## Steps

1. Read all of [`examples.md`](examples.md). The voice is the same in every kind
   of post, so every section shows it.
2. List the facts the post carries, from the source draft or the conversation.
   Name the kind of post: issue summary, or a comment that is an
   acknowledgement, status update, review, proposal, position, correction or
   scoping.
3. Write the post from the list of facts, the way Pieter would tell them to a
   colleague, at the length of its kind. Only the facts of a source draft carry
   over; its sentences are rewritten. An issue summary keeps the headings of the
   project's template, such as Drupal's `###` Problem/Motivation, Steps to
   reproduce and Proposed resolution; the voice applies to the prose under them.
4. Read the examples of its kind again, then the post, in one run. Generated
   prose shows in its rhythm: sentences that open the same way, sentences of the
   same length and shape, a connector or a phrase used again and again. Rewrite
   until the post blends in. Done when the post blends in among the examples and
   meets every [constraint](#constraints).

## Constraints

These cover what the examples cannot show, or show in a way that is not to be
copied.

- **Facts.** Every fact of the list is in the post, unchanged, and the post adds
  none.
- **Claude's work.** When the post reports work that Claude did, such as an
  investigation, a reproduction or a fix, the opening says so in plain words, as
  in the proposal "I ran into the same error and let Claude investigate it. It
  found the cause."
- **Commitments.** A promise of future work, such as "I will implement this" or
  "I can take care of that" in the examples, is written only when Pieter has
  said in the conversation that they take that work on.
- **Asking.** A question goes to a maintainer about a decision that is theirs to
  make, or to a person about a contribution they are actively working on: "Would
  it be OK to include these in the roadmap?", "@owenbush do you want to weigh
  in?" People who created or joined an issue owe it nothing further, so the post
  leaves them free of any task, including confirming or agreeing.
- **Self-contained.** The reader gets everything from this post alone. When
  something from another post matters, the post says the thing itself or quotes
  it. A comment number is only an extra, as in the correction "I was wrong in
  comment #15, the original code does a loose comparison".
- **Own work.** A report of own work opens with the result, as in "Updated code
  to work with latest 11.x." The commit or push that delivered it stays
  unmentioned.
- **Explaining a change.** A proposal first says how the existing code works at
  the place of the change, then presents the change as what we can do there:
  "When an aggregate is generated on demand, `AssetResolver::getJsAssets()`
  retrieves the list of JS assets from the cache. At this point we can check if
  the generated JS assets in the list are available on disk."
- **Ending.** The post ends on its last substantive point.

## Length

| Kind | Length |
|---|---|
| Issue summary | 20 to 150 words of prose, plus error output and code in code blocks |
| Acknowledgement | One line |
| Status update, review, scoping, correction | 20 to 80 words |
| Position | 60 to 120 words |
| Proposal | 100 to 300 words, in paragraphs, with code where it helps |

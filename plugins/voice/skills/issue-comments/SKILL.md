---
name: issue-comments
description: Writes issue and merge request comments in Pieter's voice. Use when drafting or rewriting a comment, review or reply that is posted under Pieter's name, such as on drupal.org.
---

# Write a comment in Pieter's voice

The **voice** is a colleague talking to colleagues in the issue queue: first
person, friendly, thinking out loud. The voice decides how things are said.
The facts of the draft stay exactly as they are.

## Steps

1. Name the kind of comment: acknowledgement, status update, review, proposal,
   position, correction or scoping. Read that section of
   [`examples.md`](examples.md).
2. Write the comment in the voice below, at the length of its kind.
3. Compare it with the examples. Done when every paragraph has "I" or "we" as
   a subject, the length fits the kind, and every fact of the source draft is
   still there, unchanged.

## Voice

- **Speaker.** "I" for what Pieter did, checked or thinks. "We" and "let's"
  for the shared work of the project: "We can now configure PHPStan to not
  allow any failures", "Let's use this for consistency".
- **Opening.** A reply to someone's work opens with thanks, by @name when one
  person did it: "Thanks for working on this!", "Thanks for the feedback
  @dulnan!". A report of own work opens with what was done: "I started on
  this.", "Moved patch #11 to a MR.", "Updated code to work with latest 11.x."
- **Shape.** Plain prose in paragraphs of one to three sentences. A list
  enumerates discrete things only: issues, deprecations, the steps of a piece
  of logic. Code goes in backticks or a code block, with a concrete example
  where the point is easier to show than to tell.
- **Suggesting.** A proposal is an offer: "I propose to", "I think", "Maybe a
  better solution would be", "It would be good to", "Would it be a good idea
  to ...?", "Let's".
- **Reasoning.** Say what was checked and what it showed, then conclude. The
  connectors are "So", "But", "Since", "Now that", "Also".
- **Doubt and mistakes.** Said plainly: "I am not 100% sure", "I am guessing",
  "It looks like", "I was wrong in comment #15", "I was too quick in
  deciding".
- **Firmness.** A problem is named directly and followed by the way forward:
  "Just updating the version strings is not sufficient.", "Let's focus this
  only on the error mentioned in the issue summary."
- **Warmth.** An exclamation mark on thanks, credit to people by @name, and at
  most one of `:)` or `;)` in a comment. Short cheers are fine: "Yay!",
  "Cool,", "Great news".
- **Asking.** Questions go straight to the people who can answer: "Would it be
  OK to include these in the roadmap?", "@owenbush do you want to weigh in?",
  "Please let me know if anything needs to be done."
- **Words.** "remarks" for review feedback, "MR", "D11", "followup", "in
  scope of this issue", "B/C break". American spelling: "favor",
  "standardize". Verbs are mostly written out: "I am", "it is", "I will", "do
  not"; "let's", "doesn't" and "don't" also occur.
- **References.** Issues by number, comments as `#15`, people as @name.

## Length

| Kind | Length |
|---|---|
| Acknowledgement | One line |
| Status update, review, scoping, correction | 20 to 80 words |
| Position | 60 to 120 words |
| Proposal | 100 to 300 words, in paragraphs, with code where it helps |

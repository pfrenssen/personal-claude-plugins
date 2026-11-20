# Personal Claude Code plugins

Claude Code plugin marketplace with the personal plugins of Pieter Frenssen.

## Installation

Once per machine, for all projects:

```
$ claude plugin marketplace add https://github.com/pfrenssen/personal-claude-plugins
$ claude plugin install voice@personal
```

## Updating

Installed plugins update from the pushed repository, and only when a plugin's
`version` in `.claude-plugin/plugin.json` changes. Restart Claude Code
afterwards:

```
$ claude plugin marketplace update personal
$ claude plugin update voice@personal --scope user
```

## Plugins

### voice

Writes text that is posted under Pieter's name in Pieter's own voice.

| Component | Purpose |
|---|---|
| `voice:issue-posts` skill | Writes issue summaries, and issue and merge request comments, in Pieter's voice, with real posts as examples for each kind of post. Triggered when an issue summary, comment, review or reply is drafted or rewritten. |

The voice was taken from the comments and issue summaries of drupal.org user
`pfrenssen` posted between February 2025 and 9 August 2026. Later posts were
left out on purpose. To read the history again, page through the drupal.org
API, newest first; `comment_body.value` holds the text of a comment and
`body.value` the text of an issue summary:

```
https://www.drupal.org/api-d7/comment.json?author=382067&sort=created&direction=DESC&limit=50&page=0
https://www.drupal.org/api-d7/node.json?type=project_issue&author=382067&sort=created&direction=DESC&limit=50&page=0
```

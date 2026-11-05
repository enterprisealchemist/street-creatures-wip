# Street Creatures WIP

Vito's private studio page over the board (the `board` issues in the private street-creatures repo). Four tabs:

- **Team**: the hierarchy, with each person's active tickets.
- **Board**: counts, stalled tickets, everything in flight, and the backlog (reorder it; it writes the ticket's priority).
- **Review**: open proposals (`status:proposal`). Approve or reject with a comment: it goes on the issue at once as a
  `Vito: …` comment plus a `vito-approved` / `vito-rejected` label.
- **Release**: merged, player-visible changes (issues labelled `release-note`, with a `Release:` comment and its
  capture). Good or fix with a comment, the same way (`vito-good` / `vito-fix`).

Review and Release each have a **Send to Top Cat** button: it starts the `send` Action in this repo, which comments
the decided issue numbers on the inbox PR (#12, never merged). Top Cat's session watches that PR, so the comment wakes it to run verdict_action.py and route them. It sends only issue numbers and verdict words; Top Cat reads
your comments on the private issues.

## Token

The page holds no data. Your GitHub fine-grained token is pasted once per browser and kept in that browser's local
storage, so a refresh opens straight away (Vito 10-18: no password). **Forget token** removes it. The token is only ever
sent to api.github.com. A browser still holding the old password-locked copy asks for the password once and converts it.

Token permissions: street-creatures: Issues read and write, Contents read (captures); street-creatures-wip: Actions read
and write (Send).

## Secrets

None. The `send` Action comments with the repo's own `github.token`; its input is just `#<issue> <verdict>` lines (this
repo is public, so comment text never goes through it).

Open it at https://enterprisealchemist.github.io/street-creatures-wip/ (Pages: deploy from branch `main`, root).

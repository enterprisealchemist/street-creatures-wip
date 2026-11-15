# Street Creatures WIP

Vito's private studio page over the board (the `board` issues in the private street-creatures repo). Four tabs:

- **Board**: a milestone switch (M1 / M2 / Stage 3) with a progress bar and a "left · done" count, a row per lead with
  their current batch and how recently they touched it, and count tiles that filter the lists below when clicked. A
  search box filters by id and title. The "Waiting on" view groups blocked tickets under Vito, Art and Another ticket,
  marking one whose blocker is already closed. Below are stalled tickets, everything in flight and the backlog. Click
  any ticket row to open its details (Vito's words and the Current block) and a note box: posting a note writes a
  `Vito: note — …` comment on the issue and queues it for **Send to Top Cat**.
- **Review**: open proposals (`status:proposal`). Approve or reject with a comment: it goes on the issue at once as a
  `Vito: …` comment plus a `vito-approved` / `vito-rejected` label.
- **Release**: merged, player-visible changes (issues labelled `release-note`, with a `Release:` comment and its
  capture). Good or fix with a comment, the same way (`vito-good` / `vito-fix`).
- **Canon**: rules.md and the canon/ pages, edited inline against master.

Review, Release and Board each have a **Send to Top Cat** button: it starts the `send` Action in this repo, which
comments the decided issue numbers and verdict words (including `note`) on the inbox PR (#12, never merged). Top Cat's
session watches that PR, so the comment wakes it to run verdict_action.py and route them. It sends only issue numbers
and the word; Top Cat reads your comments on the private issues.

## Token

The page holds no data. Your GitHub fine-grained token is pasted once per browser and kept in that browser's local
storage, so a refresh opens straight away (Vito 10-18: no password). (Vito 11-14: no Forget token button on the page; it was one tap from locking a phone out.) The token is only ever
sent to api.github.com. A browser still holding the old password-locked copy asks for the password once and converts it.

Token permissions: street-creatures: Issues read and write, Contents read (captures); street-creatures-wip: Actions read
and write (Send).

## Secrets

None. The `send` Action comments with the repo's own `github.token`; its input is just `#<issue> <verdict>` lines (this
repo is public, so comment text never goes through it).

Open it at https://enterprisealchemist.github.io/street-creatures-wip/ (Pages: deploy from branch `main`, root).

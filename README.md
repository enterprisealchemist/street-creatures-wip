# Street Creatures WIP

Vito's private studio page over the board (the `board` issues in the private street-creatures repo). Four tabs:

- **Team**: the hierarchy, with each person's active tickets.
- **Board**: counts, stalled tickets, everything in flight, and the backlog (reorder it; it writes the ticket's priority).
- **Review**: open proposals (`status:proposal`). Approve or reject with a comment: it goes on the issue at once as a
  `Vito: …` comment plus a `vito-approved` / `vito-rejected` label.
- **Release**: merged, player-visible changes (issues labelled `release-note`, with a `Release:` comment and its
  capture). Good or fix with a comment, the same way (`vito-good` / `vito-fix`).

Each of Review and Release has one **Send** button: it starts the `relay` Action in this repo once for the whole batch,
which fires one Claude routine (Top Cat for Review, Garfield for Release). The routine reads your comments on the issues
and messages the right session.

## Token

The page holds no data. Your GitHub fine-grained token is pasted once per browser and kept in that browser's local
storage, so a refresh opens straight away (Vito 10-18: no password). **Forget token** removes it. The token is only ever
sent to api.github.com. A browser still holding the old password-locked copy asks for the password once and converts it.

Token permissions: street-creatures: Issues read and write, Contents read (captures); street-creatures-wip: Actions read
and write (Send).

## Secrets

`TOPCAT_ROUTINE_TOKEN`, `TOPCAT_ROUTINE_URL`, `GARFIELD_ROUTINE_TOKEN` and `GARFIELD_ROUTINE_URL` (Settings → Secrets and
variables → Actions) are the API token and /fire URL of each of the two routines. Only the Action reads them. The Action's inputs are just `#<issue> <ticket>: <verdict>` lines (this
repo is public, so comment text never goes through it).

Open it at https://enterprisealchemist.github.io/street-creatures-wip/ (Pages: deploy from branch `main`, root).

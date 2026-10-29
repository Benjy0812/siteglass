# YouTube Full-Viewport Userstyle

A single Stylus userstyle, `youtube-fullviewport.user.css`, for YouTube. The user runs it in Zen (Firefox-based) through the Stylus extension.

## Workflow

- Commit a feature only after the user says it is done. Do not commit on your own after each edit.
- Bump `@version` and the `--fv-version` marker in the CSS with every change, so the user can confirm which copy Stylus is running.
- Commit messages end with the `Co-Authored-By` line from the session's attribution reminder.

## Testing notes

- YouTube serves different watch-page layouts to different accounts: a full-bleed layout (`[full-bleed-player]`) and a two-column layout (`:not([full-bleed-player])`). Keep rules scoped for both.
- Stylus on Firefox injects a user stylesheet, which does not appear in `document.styleSheets`. Verify with `getComputedStyle(document.documentElement).getPropertyValue('--fv-version')`.
- The user pastes the whole file into Stylus (Ctrl+A, paste, save) and hard-refreshes. A stale copy is the most common reason a change appears not to work.

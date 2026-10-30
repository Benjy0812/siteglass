# siteglass

Frosted, distraction-free restyling for the sites you use. Right now it ships one pack, **YouTube**, as a Stylus userstyle. A cross-browser extension with a pack per site is the plan.

## YouTube pack

`youtube-fullviewport.user.css`

- **Full-viewport player.** The video fills the window, letterboxed instead of stretched. Opening a panel never resizes it.
- **Auto-hiding header.** The whole top bar (logo, search, profile) is hidden until you hover the top edge, and it has a frosted look. The search box has no borders and a soft shadow, and the voice-search button is removed.
- **Description / Comments rail.** An icons-only frosted pill, hidden until you hover the top-right corner. It stays visible while a panel is open and docks against the panel.
- **Frosted panels.** Description and Comments open in one persistent rounded card. Switching between them only fades the contents, so the card doesn't blink.
- **Declutter.** No Shorts, filter chips, promo slots, end-screen tiles, channel watermark or card teasers.

## Install (Stylus)

1. Install [Stylus](https://github.com/openstyles/stylus) for your browser. Firefox-based browsers such as Zen work too.
2. Open Stylus and choose **Write new style**.
3. Select all, paste the contents of `youtube-fullviewport.user.css`, and **Save**.
4. Hard-refresh YouTube (`Ctrl+Shift+R`).

## Settings

Everything adjustable is a variable at the top of the file:

| Variable | Default | Controls |
|---|---|---|
| `--fv-radius` | `12px` | Corner radius of the rail and panel card |
| `--fv-hover-delay` | `.25s` | Wait before the header and rail appear on hover |
| `--fv-reach-delay` | `.1s` | Extra wait before rail buttons can be clicked (stops early tooltips) |
| `--fv-ease` | `cubic-bezier(.22, 1, .36, 1)` | Easing used by panel motion |

## Troubleshooting

- **Change not showing?** The usual cause is a stale copy in Stylus. Select all, paste the full file, save, and hard-refresh.
- **Check which version is live.** Run this in the browser console on YouTube:

  ```js
  getComputedStyle(document.documentElement).getPropertyValue('--fv-version')
  ```

- **Something looks broken after a YouTube update.** YouTube changes its markup often, and it serves different watch layouts to different accounts. The CSS handles two (full-bleed and two-column). Open an issue with a screenshot and the output of the version check.

## Known limits

- Panels can't animate **closing**: YouTube removes a closed panel instantly.
- Styles load as a user stylesheet in Firefox-based browsers, so `transition` rules need `!important` to beat YouTube's own. Comments in the file explain where this matters.

## Roadmap

- A Manifest V3 extension for Chrome, Edge and Firefox, with a content script that injects the CSS.
- Per-site **packs**, with a shared design layer for the frosted look, hover delay and easing.
- A popup with per-site and per-feature toggles, and an options page with sliders for the variables above.

# Keshav XMB personal site

A personal website styled after the PS3 XMB (cross media bar). **One self-contained file: `index.html`** (vanilla HTML/CSS/JS, no build step, no framework). The fonts (Jost, Noto Sans Tamil) and the resume PDF are embedded as base64 `<script>` blocks at the very bottom of the file. `Keshav-Thiagarajan-Resume.pdf` in this folder is just a spare copy.

## User preferences
- Keep it a single HTML file. Do not scaffold Vite/React or split into pages (the XMB needs one page for its animations). Splitting the code into css/js files was discussed but not chosen.
- Dislikes lopsided or empty layouts: everything must be balanced, symmetrical and easy to read on a computer screen. Verify layout changes with screenshots before calling them done.
- Test at 1920x1030, 1440x900, 1280x720, 1024x640 and a phone width (390x844).
- The user dictates by voice, so read requests generously.

## Layout rules (all user-approved, keep them)
- **Home:** classic XMB slide. The focused icon and the item list sit on one fixed axis and the 8-icon bar slides under it, so the list never moves sideways. The axis is placed so the bar is exactly centred when the start category (About) is focused. The list hangs to the right of the focused icon. On phones the same sliding bar is used.
- **Open pages (screens at least ~1250px wide):** mirrored three columns. Item list on the left, content centred on the screen, a matching right column (large icon tile, or game score + controls, or the focused cover). Equal outer margins. The icon bar is centred over the content with an accent underline under the active category. On narrower screens the right column hides and the content is centred in the remaining space.
- Control hints are always bottom-right. Notifications are always top-right (phones: top).
- Categories do not wrap around at the ends. Item descriptions are 15px.
- Accent colour drives everything (14x6 swatch picker in Settings > Theme Color).

## Features
- 8 categories: Settings, Fun, About, Likes, Work, Extras, Contact, Resume. Keyboard (arrows, Enter/X, Esc/Backspace/O, M to mute, PageUp/Down), mouse wheel, click and touch swipes. Deep links like `index.html#/work/evolocity`.
- Settings: Theme Color, Sound (+ volume, test), Clock (live preview), Background (9 canvas effects with live thumbnails + Off), System (intro, trophy toggles, resets). Settings persist in localStorage.
- Fun: Snake, Pong, Block Breaker, 2048, Tic-Tac-Toe, Flappy Bird (tuned easy), plus a Trophies page (15 trophies, 2 hidden, Konami code gives one). A short startup intro plays once per session.
- Likes > Games: Steam cover art from `cdn.akamai.steamstatic.com`. Likes > Movies: posters fetched from each film's Wikipedia page (`MOVIE_WIKI` list near the top of the script) and cached in localStorage. A styled title card shows if an image fails to load.

## Editing
- All text, links and contact details live in the CONTENT block near the top of the `<script>` in `index.html` (the `CATS`, `SITE`, `GAME_LIKES`, `MOVIE_LIKES` data). Search for `CONTENT:`.
- Still placeholders: Books, Music, Travel, Everyday, People. GitHub, LinkedIn and Instagram handles are dummies (an empty `href` hides the button; add a real profile URL to enable it).
- Layout maths is in `computeLayout()` / `place()`. Games are in the `GAMES` section.
- The source was written as separate parts (head/CSS, content, icons, core, layout, panels, input, games, background, boot) and concatenated into `index.html` with a PowerShell build script. That source and script live in a temporary session folder, not here, so for future edits just edit `index.html` directly.

## Publishing
- Plan: GitHub repo, then GitHub Pages (Settings > Pages > deploy from branch `main`, root). Free Pages needs a public repo. The user was weighing GitHub Desktop vs the VS Code Source Control tab (git was not installed yet).
- Note: `index.html` contains the resume PDF, email and phone number, so they are public once the site is published. The user should check the PDF for anything they do not want online (home address, referee details). I never managed to open the PDF myself, so I have not verified what it contains. If you do not want this file public, delete it before pushing.

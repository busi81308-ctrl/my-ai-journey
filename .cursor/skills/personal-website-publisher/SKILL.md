---
name: personal-website-publisher
description: Updates and publishes a personal landing page with bundled assets. Use when the user asks to edit a single-page personal website, adjust visual sections, add media or links, and publish changes to GitHub with practical push troubleshooting.
---

# Personal Website Publisher

## When To Use

Use this skill when the user wants to:

- update a personal single-page site (`index.html`)
- tweak styles, sections, media cards, sliders, or bilingual copy
- add local assets like images/videos
- publish the site to GitHub and troubleshoot push errors

## Default Assumptions

- Primary file is `index.html` in workspace root.
- CSS and JavaScript are inline unless user asks to split files.
- Keep visual style coherent (glassmorphism, soft gradients, rounded corners, soft shadows).
- Preserve existing user content unless explicitly replaced.

## Editing Workflow

1. Read `index.html` first.
2. Make focused updates:
   - structure in HTML
   - matching CSS classes
   - minimal JS for interactions
3. Keep accessibility basics:
   - meaningful button text
   - `alt` text for images
   - `aria-label` where needed
4. After edits, run lints for changed file(s).

## UI Pattern Defaults

- **Card style**: translucent white background, subtle border, rounded corners, gentle shadow.
- **Buttons**: gradient fill, soft hover lift, high contrast text.
- **Motion**: smooth transitions (`0.2s` to `0.4s`), avoid aggressive animation.
- **Responsiveness**: collapse multi-column sections to single column under mobile width.

## Media Integration Rules

- Use local relative paths (e.g., `p1.jpg`, `myvideo.mp4`).
- For sliders:
  - horizontal scroll + `scroll-snap`
  - previous/next controls with smooth scroll
- For videos:
  - `controls` enabled
  - full width within card
  - fallback text for unsupported browsers

## Bilingual Content Pattern

When user asks for Chinese/English toggle:

1. Add `data-i18n` and `data-i18n-html` markers to translatable text.
2. Create a compact dictionary object for `zh` and `en`.
3. Toggle language with one floating button.
4. Apply a short fade transition during text switch.

## Git Publish Workflow

Use this command sequence:

```bash
git add .
git commit -m "Update personal website content and styling"
git branch -M main
git push -u origin main
```

If push is rejected because remote has commits:

```bash
git pull origin main --rebase --allow-unrelated-histories
git push -u origin main
```

If push fails due to connectivity (`github.com:443`):

- verify network/proxy
- retry push
- offer GitHub web upload fallback

## Response Style

- Keep guidance concise and actionable.
- Prefer copy-paste-ready commands.
- For troubleshooting, state root cause first, then exact next command.


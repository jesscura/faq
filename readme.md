# faqseerstone

Static Knowledge Base (Clenzy / HiZoo / SLA Playbook) hosted with GitHub Pages.

## Features
- Multi-collection accordion (Clenzy, HiZoo, SLA Playbook)
- Live search (question + answer + tags)
- Filters: Collection, Category, Tag chips
- Expand / collapse all
- Accessible keyboard navigation
- Hash deep-linking (e.g. `#clenzy-pu-what-is`)
- Pure static (no build step)

## Keyboard Shortcuts
| Key | Action |
|-----|--------|
| `/` | Focus search field |
| Esc | Clear search (when search has focus) |
| Enter / Space | Toggle current question |
| Arrow Up / Down | Move within category |
| Home / End | Jump to first / last question |

## Local Usage
Just open `index.html` in a modern browser.

## Deployment (GitHub Pages)
1. Commit `index.html` to the repository root (main branch).
2. Settings → Pages → Deploy from a branch.
3. Select `main` and `/ (root)` → Save.
4. After it builds, site will be at: `https://jesscura.github.io/faqseerstone/`

## Custom Domain (Optional)
Configure a CNAME in Settings → Pages, then add a `CNAME` file with the domain, and update DNS.

## Future Ideas
- Light/dark theme toggle
- Search scoring (e.g. Lunr/Elasticlunr)
- Analytics for search queries
- Localization (external JSON for strings)
- Copy link button per question

## License
MIT (add a LICENSE file if desired).
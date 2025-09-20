# faq

Static Knowledge Base (multi-collection FAQ).  
Automatically deployed to GitHub Pages via Actions (default GitHub domain, no custom domain configured).

## Live URL
`https://jesscura.github.io/faq/` (available after first successful workflow run)

## Features
- Multi-collection structure (e.g., product areas / playbooks)
- Live text search across questions, answers, and tags
- Filters: collection, category, tag chips (tags use AND logic)
- Expand / Collapse all visible items
- Accessible keyboard navigation (aria-expanded, roles, focus handling)
- Deep linking to individual FAQ items via hash anchors
- Pure static single-file implementation (`index.html` + embedded data)
- Tailwind via CDN (no build pipeline)

## Keyboard Shortcuts
| Key | Action |
|-----|--------|
| `/` | Focus search field |
| Esc | Clear search (when search focused) |
| Arrow Up/Down | Navigate questions in current category |
| Home / End | Jump to first / last question |
| Enter / Space | Toggle focused question |

## Deployment (Automated)
A GitHub Actions workflow (`.github/workflows/pages.yml`) deploys the repository root to GitHub Pages on every push to `main` (and on manual dispatch).  
Source: GitHub Actions (not a branch).  
No custom domain / no `CNAME` file.

### Verifying Deployment
1. Actions tab → latest “Deploy GitHub Pages” run succeeds.
2. Visit the Live URL.
3. Settings → Pages shows environment bound to the workflow.

## Re-Adding a Custom Domain (Optional Future)
1. Add a `CNAME` file with: `your.domain.com`
2. Settings → Pages → Custom domain: enter same domain.
3. DNS:
   - Apex: A records → 185.199.108.153 / 185.199.109.153 / 185.199.110.153 / 185.199.111.153
   - Subdomain: CNAME → `jesscura.github.io`
4. Wait for TLS provisioning.  
Remove by deleting `CNAME` + clearing the Pages custom domain field.

## Editing FAQ Content
All FAQ data resides in a `DATA` object inside `index.html`.

Add a new FAQ item:
```js
{
  id: "collection-slug-new-topic",
  question: "What is the new feature?",
  answer: "Concise explanation...",
  tags: ["tag1", "tag2"]
}
```
Guidelines:
- `id` must be unique, stable (for deep links), kebab-case.
- Keep answers concise; use paragraphs / lists only if needed.

## Enhancement Ideas
- Externalize dataset to `data.json` (fetched at runtime)
- Dark / Light theme toggle (prefers-color-scheme + manual toggle)
- Lunr.js or MiniSearch relevance scoring
- Analytics events (search queries, expansions)
- Copy link button per question
- Offline caching with a Service Worker
- Split large `index.html` into separate JS + JSON modules

## Contributing
Create a feature branch → open a PR with a clear description.  
For larger shifts (framework migration, data externalization) open an issue first.

## License
MIT (add a LICENSE file if desired).

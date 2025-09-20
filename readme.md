# faqseerstone

Static Knowledge Base for Clenzy, HiZoo, and the SLA Playbook.  
Deployed automatically to GitHub Pages (default GitHub domain, no custom domain configured).

## Live URL
`https://jesscura.github.io/faqseerstone/` (after first successful workflow run)

## Features
- Multi-collection organization (Clenzy / HiZoo / SLA Playbook)
- Live text search (questions + answers + tags)
- Filters: Collection, Category, Tag chips (AND logic for tags)
- Expand / Collapse all visible items
- Accessible keyboard navigation (aria-expanded, region roles)
- Hash deep linking per FAQ item (`#clenzy-pu-what-is`)
- Pure static (single `index.html`) – no build step required
- Tailwind via CDN

## Keyboard Shortcuts
| Key | Action |
|-----|--------|
| `/` | Focus search field |
| Esc | Clear search (when search box focused) |
| Arrow Up/Down | Navigate within category |
| Home / End | Jump to first / last question |
| Enter / Space | Toggle focused question |

## Deployment (Automated)
Deployment is handled by GitHub Actions (`.github/workflows/pages.yml`).  
On each push to `main` (or manual dispatch) the repository root is published to Pages.  
Source: GitHub Actions (not direct branch).  
No custom domain or `CNAME` file is present.

### Verify
1. Open the Actions tab → latest “Deploy GitHub Pages” run should succeed.
2. Visit the live URL above.
3. Settings → Pages should show the environment linked to the workflow.

## Re-Adding a Custom Domain (Optional)
If you decide to use one later:
1. Add `CNAME` file with a single line: `your.domain.com`
2. Settings → Pages → Custom domain: enter the same domain.
3. DNS:  
   - Apex: A records to `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`  
   - Subdomain: CNAME to `jesscura.github.io`
4. Wait for TLS certificate provisioning.
To remove again: delete `CNAME` + clear setting.

## Editing Content
All data lives in the `DATA` object inside `index.html`.  
Add a new item by appending an object with unique `id`, `question`, `answer`, and `tags` to the correct category’s `items` array.

Example:
```js
{
  id: "clenzy-new-topic",
  question: "New question?",
  answer: "Clear, concise answer.",
  tags: ["tag1","tag2"]
}
```

## Enhancement Ideas
- Externalize dataset to `data.json`
- Dark/light theme toggle
- Lunr.js search scoring
- Analytics hooks (search queries, expansions)
- Copy link button beside each question
- Offline Service Worker caching

## Contributing
Open a PR with a concise description.  
For large structural changes (framework migration, theming engine) start an issue first.

## License
MIT (add LICENSE file if needed).

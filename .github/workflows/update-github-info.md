---
name: update-github-info
description: Review official GitHub Blog and Changelog updates and propose practical updates for the GitHub Info site.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: read
  copilot-requests: write
engine:
  id: copilot
  copilot-sdk: true
strict: true
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    max: 1
    draft: false
    title-prefix: "[Mona review] "
    allowed-files:
      - site/content/github-info.md
---

# Update GitHub Info

Read `notes/mona-notes.md` and `site/content/github-info.md` before making changes. Follow Mona's editorial guidance: keep updates short and practical, focus on helping developers learn GitHub, and attribute material from official sources.

Use `web-fetch` to read both:

- https://github.blog/latest/
- https://github.blog/changelog/

Select only recent, useful items that fit the site's existing themes. Verify details against the fetched pages, avoid repeating existing material, and do not invent facts. Update only `site/content/github-info.md`; preserve its existing structure and voice.

Review the final diff for accuracy, concise wording, and source links. If there is no meaningful update, make no changes and do not open a pull request. Otherwise, open one pull request containing only the site content change. Explain the selected updates and cite their official source URLs in the PR description. Address the PR to Mona for review, and do not publish or write directly to the default branch.
---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
network:
  allowed:
    - github.blog
    - github.com
tools:
  edit:
  web-fetch:
  github:
    toolsets: [repos]
safe-outputs:
  create-pull-request:
    max: 1
    draft: true
---

# Update GitHub Info

Keep the GitHub Info content current for Mona's review.

## Instructions

1. Read `notes/mona-notes.md` first and follow its editorial guidance.
2. Read the current `site/content/github-info.md`.
3. Use the `web-fetch` tool to read the latest public guidance from `https://github.blog/latest/`.
4. Use the `web-fetch` tool to read the latest public guidance from `https://github.blog/changelog/`.
5. Use the GitHub repository API tools to read repository guidance or reference files. Do not use terminal commands, the GitHub CLI, or sandboxed commands for those repository reads.
6. Update `site/content/github-info.md` with short, practical guidance backed by the official sources. Preserve the existing editorial angle and mention the source for each blog or changelog-based update.
7. Make only focused content changes that are supported by the sources. If there is nothing useful to add or update, leave the file unchanged.
8. When changes are needed, use the `create-pull-request` safe output to open one pull request containing the proposed update for Mona to review. Do not write directly to the default branch.

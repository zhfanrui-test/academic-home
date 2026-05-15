# GitHub Issue Academic Homepage

A lightweight academic homepage that renders profile metadata and Markdown content from a GitHub Issue.

The page looks for the latest open issue labeled `page-home`, reads the YAML front matter at the top of the issue body, and renders the remaining Markdown as the homepage content.

## How It Works

1. Create a GitHub Issue using the `Homepage` issue template.
2. Keep the `page-home` label on that issue.
3. Fill in the YAML profile fields and Markdown sections.
4. Open `index.html` in a browser.
5. The page fetches the issue and renders the homepage.

## Issue Format

The issue body must start with YAML front matter:

```yaml
---
name: "Your Name"
title: "Your Name"
bio: "A short one-sentence bio."
position: "Your Position"
institution: "Your Institution"
location: "City, Country"
avatar: "https://example.com/avatar.jpg"
email: "you@example.com"
googlescholar: "https://scholar.google.com/citations?user=YOUR_ID"
orcid: "https://orcid.org/0000-0000-0000-0000"
github: "your-github-username"
linkedin: "https://www.linkedin.com/in/your-linkedin-id"
---
```

Everything after the YAML block is rendered as Markdown.

## Supported Fields

- `name`: Display name in the profile card.
- `title`: Browser tab title source.
- `bio`: Short profile summary.
- `position`: Job title or academic position.
- `institution`: Affiliation.
- `location`: City or country.
- `avatar`: Profile image URL.
- `email`: Email link.
- `googlescholar`: Google Scholar profile URL.
- `orcid`: ORCID profile URL.
- `github`: GitHub username or URL.
- `linkedin`: LinkedIn profile URL.

## Navigation

The right-side contents navigation is generated automatically from Markdown `#` and `##` headings.

## Configuration

Edit `CONFIG` in `index.html`:

```js
const CONFIG = {
  defaultRepo: "owner/repo",
  label: "page-home",
  issueNumber: null
};
```

Set `issueNumber` if you want to load one fixed issue. Leave it as `null` to load the most recently updated open issue with the `page-home` label.

## Files

- `index.html`: The homepage app.
- `.github/ISSUE_TEMPLATE/homepage.md`: GitHub Issue template for homepage content.

## Notes

GitHub API rate limits may apply for unauthenticated requests. For a public repository and light usage, the default setup is usually enough.

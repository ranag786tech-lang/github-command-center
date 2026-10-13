# GitHub Command Center v1.0

A local-first, single-file developer productivity dashboard prototype.

## What's included

- Responsive dashboard with sample repository and activity data
- Repository list with language filtering
- Sample issues and pull-request triage table with filters
- Local repository-health checklist
- README Markdown starter generator
- `.gitignore` builder
- License-template generator
- Changelog builder
- JSON formatter, validator, and minifier
- Basic GitHub Actions YAML text checks
- Git command builder
- GitHub Actions workflow starter generator
- Dark and light themes
- Download generated files directly from the browser

## Run locally

### Option A: Open the file

1. Download `github-command-center-v1.html`.
2. Open it in a modern browser (Chrome, Edge, Firefox, or Safari).
3. Use the sidebar to switch modules.
4. Use the sun/moon button in the top bar to switch themes.

No package installation, build step, backend, API key, or GitHub login is needed for v1.0.

### Option B: Serve it locally

From the folder containing the file, run:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000/github-command-center-v1.html`.

## Architecture

This prototype uses a single HTML document:

- **Structure:** semantic HTML for the sidebar, header, dashboard, and tool panels
- **Styles:** CSS custom properties for themes, responsive layout, cards, tables, and forms
- **Application state:** small in-memory JavaScript state object for current page, selected tool, filters, and generated output
- **Local tools:** browser-side JavaScript functions generate Markdown, ignore patterns, license templates, changelogs, JSON output, Git commands, and workflow YAML
- **Persistence:** the theme preference is stored in `localStorage` when available
- **Demo data:** repositories, activity, issues, and pull requests are illustrative hard-coded sample records

## Important limitations

- Repository, issue, pull-request, and health dashboard data are demo data; the app is not connected to GitHub.
- The YAML checker is a heuristic text check, not a complete YAML parser or GitHub Actions validator.
- The health checklist is a guide, not a source-code, dependency, or secret scanner.
- License output is a starting template. Review the complete official license terms before distributing a project.
- Git command and workflow generators produce text only; they do not run commands or deploy anything.
- The prototype does not save generated content automatically.

## Phase 2: GitHub integration

A production integration should add:

1. A GitHub App or appropriate OAuth flow.
2. A backend/session layer for securely handling credentials; never ship an app client secret in browser code.
3. Explicit, least-privilege permissions for repository metadata, issues, and pull requests.
4. API client functions separated from UI components.
5. Loading, error, empty, pagination, and rate-limit states.
6. Tests for API responses and permissions.
7. A clear disconnect/revoke-access flow.

Suggested future structure:

```text
github-command-center/
├── app/                 # UI routes and layouts
├── components/          # Reusable cards, tables, forms
├── features/
│   ├── repositories/    # Repository views and health checks
│   ├── issues/          # Issue and pull-request triage
│   └── tools/           # Local generators
├── lib/
│   ├── github/          # GitHub API client (Phase 2)
│   └── validators/      # JSON/YAML/config checks
├── tests/
├── public/
└── README.md
```

## Suggested repository setup

1. Create a GitHub repository named `github-command-center`.
2. Add the HTML file as `index.html` if you want to publish it with GitHub Pages.
3. Add this README as `README.md`.
4. Commit and push the files.
5. In repository Settings → Pages, configure deployment from your chosen branch/folder if GitHub Pages is appropriate for the repository.

For the standalone prototype, static hosting is enough. Do not add GitHub credentials or private tokens to the HTML file.
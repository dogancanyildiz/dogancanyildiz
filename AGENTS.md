# AGENTS.md

## Repository overview

This is a **GitHub profile README repository** (`dogancanyildiz/dogancanyildiz`). GitHub renders `README.md` on the owner's profile page. There is no application, backend, database, or build system here.

Contents:
- `README.md` — the profile page (Markdown + external badge/stat image services, mostly Turkish).
- `.github/workflows/snake.yml` — a scheduled GitHub Actions workflow (`Platane/snk`) that generates a contribution-graph "snake" SVG and force-pushes it to the `output` branch. It runs only on GitHub CI, not locally.

## Cursor Cloud specific instructions

There are no code dependencies, no package manager, and nothing to compile. The "product" is the rendered Markdown profile page. The dev workflow is: edit `README.md`, preview it as GitHub would render it, and lint the workflow YAML.

Dev tooling (installed by the update script via pip, into `~/.local/bin`):
- `grip` — GitHub Readme Instant Preview. Renders `README.md` through GitHub's markdown API into a locally-served, GitHub-styled page.
- `yamllint` — lints `.github/workflows/*.yml`.

Because `~/.local/bin` is not on `PATH` by default, invoke the tools module-style:

- Preview the profile (the "app"): `python3 -m grip README.md 0.0.0.0:6419`, then open `http://localhost:6419/`. grip re-renders on each page reload, so editing `README.md` and refreshing the browser shows changes (no restart needed).
- Lint the workflow: `python3 -m yamllint -d relaxed .github/workflows/snake.yml`.
  - Note: the workflow currently has pre-existing cosmetic lint findings (trailing spaces / blank line). These are harmless and GitHub Actions accepts the file; do not "fix" them unless asked.

Preview caveats (expected, not bugs):
- `grip` needs network access to GitHub's markdown API. Without a `GITHUB_TOKEN` it works but is rate-limited; pass `--user <name> --pass <token>` or set a token if you hit HTTP 403.
- Two images will not load in the local preview: the "Trophies" badge (a third-party service that may rate-limit) and the "Katkı Yılanı" snake SVG (its `raw.githubusercontent.com/.../output/...` URL only exists after the `snake.yml` workflow runs on GitHub). All other badges/stats load normally.

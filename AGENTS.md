# AGENTS.md

This is the profile README repository for github.com/dogancanyildiz. GitHub
renders `README.md` on the profile page; there is no app, build or test suite.

## Layout

- `README.md`: the page. English, same visual system as www.dogancanyildiz.com
  (Geist type, hairline rules, one green: `#4fcc8d` on dark, `#007041` on light).
  Dark and light variants of every image go through `<picture>` with
  `prefers-color-scheme`.
- `assets/hero-*.svg`, `footer-*.svg`, `divider-*.svg`: hand written SVGs,
  animated with SMIL (typed terminal lines, blinking cursor), fonts embedded as
  data URIs so they render inside GitHub's image proxy with no external
  request. Generated from a script kept with the site repo; edit the text
  there rather than by hand.
- `assets/stats/*.svg`: github-readme-stats cards cached as files by
  `.github/workflows/stats-cards.yml` (daily, best effort: a failed fetch keeps
  the previous file).
- `assets/snake/*.svg`: contribution snake from `.github/workflows/snake.yml`.
- The post list between `BLOG-POST-LIST` markers is written by
  `.github/workflows/blog-posts.yml` from the site's English RSS feed.

## Rules

- No em dashes anywhere. No AI attribution in commits or PRs.
- Facts (employer, city, stack, projects) follow the site; when the site
  changes, change here too. Do not add services that need a paid plan or
  that fail `curl -f` regularly (the activity graph did, it was removed).
- Preview locally with `python3 -m grip README.md` if needed; animated SVGs
  only animate when embedded as `<img>`, which grip does.

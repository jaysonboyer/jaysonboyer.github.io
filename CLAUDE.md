# jaysonboyer.github.io

Jekyll site served by GitHub Pages from `main`. A push to `main` is a publish: GitHub's built-in `pages-build-deployment` run does the build. No custom workflow, no branches, no PRs. Commit straight to `main` and push.

## When asked to publish

1. **Preview first.** macOS system Ruby is too old, so build in Docker:
   ```sh
   script/serve        # live at http://localhost:4000
   ```
   or a one-shot build check:
   ```sh
   docker run --rm -v "$PWD":/srv/jekyll -v jekyll-bundle:/usr/local/bundle -w /srv/jekyll ruby:3.3 \
     sh -c 'bundle install --quiet && bundle exec jekyll build -d /tmp/out --quiet && ls /tmp/out'
   ```
   The human looks at the preview before anything is pushed.
2. **Commit on `main`** with a message that says what changed on the site, then `git push`.
3. **Verify.** Pages builds in about a minute: `gh run list --limit 1` should show success, and the page should be live at https://jaysonboyer.github.io.

Never commit `_site/`, `.jekyll-cache/` or `Gemfile.lock`; they are gitignored.

The Pages build renders every `.md` file as a page, even without frontmatter, and the local Docker build does not. Any markdown that is not a page (this file, README) goes in the `exclude:` list in `_config.yml`, or Liquid in it breaks the live build.

## What lives where

| Path | Role |
|---|---|
| `index.md` | home page copy |
| `resume.md` | public general resume at `/resume/`. Its source of truth is `_shared/master-library.md` in the `resumes` repo; edit there first, then pull bullets in here. From the `resumes` repo, `npm run publish-site` commits and pushes only this file. |
| `_drafts/` | unpublished posts. Jekyll ignores this folder. |
| `_posts/` | published posts, named `YYYY-MM-DD-slug.md`. Currently empty on purpose. |
| `_layouts/home.html` | the post list is wrapped in `{% comment %}` until there is a real post. Remove the two comment lines when publishing the first one. |
| `_layouts/`, `_includes/`, `_sass/`, `assets/` | the vendored hacker theme (CC0, see `THEME-LICENSE`). Edit directly; there is no `theme:` key. |
| `_config.yml` | title, description, nav links |

## Publishing a blog post

1. Write it in `_drafts/`.
2. Move it to `_posts/YYYY-MM-DD-slug.md` with that date in its frontmatter.
3. Un-comment the post list in `_layouts/home.html`.
4. Follow "When asked to publish" above; `script/serve` now shows the post on the home page.

## Rules

- Nothing is pushed until a person has looked at the preview.
- Resume claims trace to the master library in the `resumes` repo, never invented here.
- Don't rewrite the theme; change the one file the request touches.

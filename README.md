# Dongseob Kim portfolio

Personal portfolio and writing site built with Jekyll and the [Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes) theme. It is intended for GitHub Pages at `eastskim48.github.io`.

## Content

- Short introduction, selected work, and interests: `index.html`
- Writing index: `_pages/writing.html`
- Blog posts: `_posts/YYYY-MM-DD-title.md`
- Local-only post drafts: `_drafts/` (excluded from Git)
- Navigation: `_data/navigation.yml`
- Colors and layout: `assets/css/main.scss`
- Public CV PDF: `assets/cv/Dongseob_Kim_CV.pdf`

The linked CV retains the author's original CV content and layout. It is a standalone PDF of the CV portion of the source draft. The website introduction is intentionally brief.

To add a post, copy `scripts/post-template.md` to `_drafts/your-title.md`, update its front matter, and write the body. Review it before moving it to `_posts/YYYY-MM-DD-title.md`. The Writing page and RSS feed update automatically after deployment.

## Local preview

Use Ruby 3.3 or a compatible version:

```sh
bundle install
bundle exec jekyll serve
```

Open `http://localhost:4000`. The GitHub Actions workflow builds the site and publishes the generated files to the `gh-pages` branch used by GitHub Pages.

## Content boundary

The website body is limited to public project facts. The linked CV retains the author's original contact details and research-status entries by explicit choice. Review new posts before publishing if they discuss work that is not already public.

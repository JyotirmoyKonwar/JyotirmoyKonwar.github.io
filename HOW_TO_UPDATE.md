# How to Update This Site

This is a Jekyll site built on the [al-folio](https://github.com/alshedivat/al-folio) theme and hosted on GitHub Pages at <https://jyotirmoykonwar.github.io>. Every push to `main` triggers the **Deploy site** GitHub Action, which builds the site and publishes it to the `gh-pages` branch. You never edit `gh-pages` or `_site/` by hand.

## Where everything lives

| What you want to change                       | File(s)                                                                            |
| --------------------------------------------- | ---------------------------------------------------------------------------------- |
| Home page bio, subtitle, contact block        | [`_pages/about.md`](_pages/about.md)                                               |
| Profile photo                                 | [`assets/img/prof_pic.jpg`](assets/img/prof_pic.jpg) (replace, keep the name)      |
| CV page (experience, education, awards, etc.) | [`_data/cv.yml`](_data/cv.yml)                                                     |
| Downloadable resume PDF on the CV page        | [`assets/pdf/Jyotirmoy_Konwar_Resume.pdf`](assets/pdf/Jyotirmoy_Konwar_Resume.pdf) |
| Projects page (one file per project)          | [`_projects/`](_projects/)                                                         |
| Project categories shown on the projects page | `display_categories` in [`_pages/projects.md`](_pages/projects.md)                 |
| Publications                                  | [`_bibliography/papers.bib`](_bibliography/papers.bib)                             |
| Social icons (GitHub, LinkedIn, email)        | [`_data/socials.yml`](_data/socials.yml)                                           |
| Site name, description, keywords, footer      | top of [`_config.yml`](_config.yml)                                                |
| Which pages appear in the navbar              | `nav: true/false` and `nav_order` in each file in [`_pages/`](_pages/)             |

## Common updates

### Update the resume PDF

The PDF comes from the LaTeX resume at `~/Desktop/Projects/resume/AI/main.tex`.

```bash
cd ~/Desktop/Projects/resume/AI && pdflatex main.tex
```

```bash
cp ~/Desktop/Projects/resume/AI/main.pdf ~/Desktop/Projects/JyotirmoyKonwar.github.io/assets/pdf/Jyotirmoy_Konwar_Resume.pdf
```

The PDF icon next to the "CV" title links to this file (set by `cv_pdf:` in [`_pages/cv.md`](_pages/cv.md)).

When the resume content changes, update [`_data/cv.yml`](_data/cv.yml) too: the CV web page is rendered from that YAML, not from the PDF.

### Add a job or internship

Add an entry at the top of `sections.Experience` in [`_data/cv.yml`](_data/cv.yml):

```yaml
- company: Company Name
  position: Your Role
  location: City, Country
  start_date: 2026-05 # only the year is displayed
  end_date: 2026-07 # leave out for "Present"
  highlights:
    - One bullet per line. **Markdown bold** works.
```

Also mention it in the bio in [`_pages/about.md`](_pages/about.md) if it is important.

### Add an award or achievement

Add to `sections.Awards` in [`_data/cv.yml`](_data/cv.yml):

```yaml
- title: Hackathon Name 2026
  date: 2026
  awarder: Organizer
  url: https://link-to-proof # optional
  summary: Winner.
```

### Add a project

1. Create a new file in [`_projects/`](_projects/), e.g. `_projects/my_new_project.md`:

   ```markdown
   ---
   layout: page
   title: My New Project
   description: One-line summary shown on the project card.
   img: assets/img/4.jpg
   importance: 1
   category: Agentic AI
   giscus_comments: false
   ---

   What it does and the results, in a short paragraph.

   - Key highlight with **numbers**.

   ### Tech Stack

   - Python, PyTorch, ...

   ### Links

   - **GitHub Repository**: [repo_name](https://github.com/JyotirmoyKonwar/repo_name)
   ```

2. `category` must be one of the names in `display_categories` in [`_pages/projects.md`](_pages/projects.md) (currently `LLM Training`, `Agentic AI`, `Machine Learning`), otherwise the project will not show up. To add a new category, add it to that list.
3. `importance` orders projects inside a category (1 = first).
4. `img` is the card image. Put your own image in `assets/img/` (a screenshot or diagram works well) and reference it here; images `1.jpg` to `12.jpg` are stock placeholders.
5. Optionally add a short entry to `sections.Projects` in [`_data/cv.yml`](_data/cv.yml) so it also appears on the CV page.

To remove a project, delete its file from `_projects/` (and its entry in `_data/cv.yml`).

### Add a publication

Add a BibTeX entry to [`_bibliography/papers.bib`](_bibliography/papers.bib):

```bibtex
@inproceedings{konwar2027example,
  abbr={EMNLP},
  bibtex_show={true},
  title={Paper Title},
  author={Konwar, J. and Coauthor, A.},
  booktitle={Proceedings of ...},
  year={2027},
  pdf={https://arxiv.org/pdf/xxxx.xxxxx},
  selected={true}
}
```

Your name is bolded automatically (configured under `scholar:` in [`_config.yml`](_config.yml)). Also add it to `sections.Publications` in [`_data/cv.yml`](_data/cv.yml).

### Change the bio or photo

Edit the text below the `---` front matter in [`_pages/about.md`](_pages/about.md). The `subtitle:` line is the tagline under your name. Replace [`assets/img/prof_pic.jpg`](assets/img/prof_pic.jpg) to change the photo.

### Turn the blog back on

The blog page exists but is hidden. Set `nav: true` in [`_pages/blog.md`](_pages/blog.md) and add posts to a new `_posts/` folder, named `YYYY-MM-DD-title.md`:

```markdown
---
layout: post
title: My First Post
date: 2026-10-16
description: Short summary.
tags: llm agents
---

Post content in Markdown.
```

## Preview locally

With Docker running:

```bash
docker compose up
```

Then open <http://localhost:8080>. The site reloads as you save files. Stop it with `docker compose down`.

## Format and publish

The **Prettier** GitHub Action fails if files are not formatted, so format before committing:

```bash
npx prettier . --write
```

```bash
git add -A && git commit -m "Update portfolio" && git push
```

After pushing, check the **Actions** tab on GitHub. When **Deploy site** turns green, the changes are live within a minute or two.

## Troubleshooting

- **Build fails with a YAML error:** a value contains `:` or starts with a special character. Wrap it in quotes, e.g. `title: "Project: Part 2"`. Indentation in `_data/cv.yml` must use spaces, not tabs.
- **A project does not appear:** its `category` does not match any entry in `display_categories`.
- **Changes are not visible:** wait for the Deploy action to finish, then hard-refresh (Ctrl+Shift+R).
- **Theme questions:** see [`CUSTOMIZE.md`](CUSTOMIZE.md), [`INSTALL.md`](INSTALL.md), and [`TROUBLESHOOTING.md`](TROUBLESHOOTING.md), or the [al-folio repository](https://github.com/alshedivat/al-folio).

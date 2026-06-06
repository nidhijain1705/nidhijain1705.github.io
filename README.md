# Nidhi Jain — personal website

This is the source for the site published at **https://nidhijain1705.github.io**.

It is built with [Quarto](https://quarto.org). You write pages in plain text (Markdown),
Quarto turns them into the website, and GitHub publishes it automatically every time you
save a change. You do not need to know HTML or web development to keep it running.

---

## How publishing works

1. You edit a file (for example, change a line in `index.qmd`).
2. You commit and push the change to the `main` branch — either from your computer, or
   directly in the GitHub website by editing a file and clicking **Commit changes**.
3. A GitHub Action (see `.github/workflows/publish.yml`) rebuilds the site and publishes it.
   The live site updates in about one to two minutes.

You can watch a build happen under the repository's **Actions** tab.

---

## One-time setup (do this once, after the first push)

GitHub needs to be told to publish from the Action:

1. In the repository, go to **Settings → Pages**.
2. Under **Build and deployment → Source**, choose **GitHub Actions**.

That's it. From then on, every push to `main` republishes the site.

---

## Editing the site

All the pages are the `.qmd` files in the top folder. Each one is mostly plain text.

| To change… | Edit this file |
|---|---|
| The bio / front page | `index.qmd` |
| Publications and working papers | `research.qmd` |
| Teaching record | `teaching.qmd` |
| The CV page | `cv.qmd` |
| Email and profile links | `contact.qmd` |
| Site title, menu, footer | `_quarto.yml` |
| Colours and fonts | `theme.scss` and `styles.css` |

### Add a paper

Open `research.qmd` and copy one of the existing `<div class="es-paper"> … </div>` blocks,
then change the year, title, and co-authors. To make a paper title link to a PDF or page,
wrap the title text in a link, e.g. `<a href="https://...">Title here</a>`.

The four papers shown on the front page are a hand-picked "selected work" list living in
`index.qmd`. Update that separately if you want the highlights to change.

### Add a blog post

1. Copy the folder `posts/welcome` and rename the copy (e.g. `posts/my-new-post`).
2. Open the `index.qmd` inside it and change the `title`, `date`, and `description` at the top,
   then write your post below. Mathematics works with `$ ... $` (inline) and `$$ ... $$` (display).
3. Commit and push. The post appears on the **Blog** page automatically, newest first.

You can delete `posts/welcome` once you've written a real post.

### Replace the CV

Put the new PDF at `assets/cv/CV_NidhiJain.pdf` (same name), commit, and push. The CV page
and the footer link will point to the new file. If you use a different file name, update the
links in `cv.qmd` and the footer block in `_quarto.yml`.

---

## Things to fill in (search for `TODO`)

- **Google Scholar** — in `contact.qmd` and the footer in `_quarto.yml`, replace
  `https://scholar.google.com/` with your real profile URL.
- **ORCID** — in `contact.qmd`, replace `https://orcid.org/` with your ORCID URL, or delete
  that line if you don't use one.

---

## Previewing on your own computer (optional)

You don't have to — pushing to GitHub is enough — but if you want to see changes before
publishing:

1. Install Quarto from <https://quarto.org/docs/get-started/>.
2. In a terminal, from this folder, run:

   ```
   quarto preview
   ```

   It opens the site in your browser and refreshes as you edit.

---

## Using a custom domain later (e.g. nidhijain.com)

If you buy a domain and want the site at `https://nidhijain.com` instead of the github.io
address:

1. Add a file named `CNAME` (no extension) in the top folder, containing just your domain:

   ```
   nidhijain.com
   ```

2. At your domain registrar, set DNS records:
   - Four `A` records for the apex domain (`nidhijain.com`) pointing to GitHub's IPs:
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - One `CNAME` record for `www` pointing to `nidhijain1705.github.io`
3. In **Settings → Pages → Custom domain**, enter the domain and tick **Enforce HTTPS**.

The github.io address keeps working and redirects to the custom domain.

---

## File map

```
_quarto.yml            site configuration (title, menu, footer, theme)
index.qmd              home page
research.qmd           publications + working papers
teaching.qmd           teaching record
cv.qmd                 CV page (links the PDF)
contact.qmd            contact details and links
blog.qmd               blog index (auto-lists posts)
posts/                 one folder per blog post
theme.scss             palette, fonts, navbar, footer
styles.css             home-page and paper-row styling
head-custom.html       loads the web fonts
assets/cv/             the CV PDF
assets/favicon.svg     browser-tab icon
.github/workflows/     the auto-publish Action
```

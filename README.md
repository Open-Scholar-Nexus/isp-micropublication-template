# ISP Micropublication Template

This repo contains a template for creating Impact Scholars Program micropublications using [MyST Markdown](https://mystmd.org/).

## Setup

We expect you to have a working conda/mamba setup. For guidance on this, see the [Conda/Mamba Tutorial](https://open-scholar-nexus.github.io/oaktree-sapling/conda-tutorial).

Install MyST Markdown using the provided environment file:

```bash
mamba env create -f environment.yml
mamba activate isp-paper
```

## Quick Start

1. **Edit your content** in `index.md`:
   - Update the `title` and `abstract` in the frontmatter (between `---` markers)
   - Write your manuscript in the main body
   - Reference your figure using `@figure-main`

2. **Add your figure**: Replace `figure.png` with your actual figure

3. **Update author information** in `myst.yml`:
   - Add author names, affiliations, and ORCID identifiers
   - Update the `title` to match your `index.md`
   - Add your keywords
   - Update github repository

4. **Add references** using either DOI (`[](doi:10.1016/j.wem.2022.09.005)`) or adding them to `bib.bib` and cite them using `@citationKey`

5. **Replace the thumbnail** in `thumbnails/thumbnail.png` for the gallery display

6. **Preview locally**:
   - While you're working on the paper, the best option is to run `myst start`
   - Before pushing, check that the static build (more detail in optional reading) is working as expected

   ```bash
   myst build --typst && myst build --html && npx serve _build/html
   ```
7. Update this README.md:
   - Include any information that someone reaching the repository may need. You can keep this README if you prefer, it won't be rendered.

## File Structure

| File | Purpose |
|------|---------|
| `environment.yml` | Conda/mamba environment for MyST |
| `index.md` | Your paper content |
| `myst.yml` | Metadata: authors, title, keywords, DOI |
| `bib.bib` | Bibliography in BibTeX format |
| `figure.png` | Your main figure (max 6 panels) |
| `thumbnails/thumbnail.png` | Gallery thumbnail image |

---

## I want to know more!

We've outlined some technical details [here](https://open-scholar-nexus.github.io/oaktree-sapling/myst-deeper).


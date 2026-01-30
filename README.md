# ISP Micropublication Template

A template for creating Impact Scholars Program micropublications using [MyST Markdown](https://mystmd.org/).

## Setup

Install MyST Markdown using the provided environment file:

```bash
mamba env create -f environment.yml
mamba activate isp-paper
```

## Quick Start

1. **Edit your content** in `index.md`:
   - Update the `title` and `abstract` in the frontmatter (between `---` markers)
   - Write your description in the main body
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

## File Structure

| File | Purpose |
|------|---------|
| `environment.yml` | Conda/mamba environment for MyST |
| `index.md` | Your paper content |
| `myst.yml` | Metadata: authors, title, keywords, DOI |
| `references.bib` | Bibliography in BibTeX format |
| `figure.png` | Your main figure (max 6 panels) |
| `thumbnails/thumbnail.png` | Gallery thumbnail image |

---

## Technical Details (Optional Reading)

### How MyST Configuration Works

This template uses MyST's configuration inheritance system. The `myst.yml` file extends shared configurations:

```yaml
extends:
  - https://raw.githubusercontent.com/pollomarzo/scholar-nexus/main/nexus.yml
  - https://raw.githubusercontent.com/pollomarzo/scholar-nexus-paper-config/main/climatematch-2023.yml
```

- **`nexus.yml`**: Provides Scholar Nexus branding and navigation
- **`climatematch-2023.yml`**: Venue-specific settings (license, funding acknowledgment)

These base configs also extend `paper-base.yml`, which configures:
- Thumbnail location for the paper gallery
- Typst PDF export settings
- Site theme options

See [MyST Configuration Documentation](https://mystmd.org/guide/configuration) for details.

### Frontmatter

The `index.md` frontmatter defines page-level metadata:

```yaml
---
title: Your Paper Title
abstract: |
    Your abstract here...
---
```

This is separate from `myst.yml` project metadata. See [MyST Frontmatter Guide](https://mystmd.org/guide/frontmatter).

### Citations

Add references to `references.bib` in BibTeX format, then cite using:
- `@citationKey` for inline citations
- `[@citationKey]` for parenthetical citations

See [MyST Citations Guide](https://mystmd.org/guide/citations).

### Figures

Figures use MyST's figure directive:

```markdown
​```{figure} figure.png
:name: figure-main
:alt: Description for accessibility

**A.** Panel A description.
**B.** Panel B description.
​```
```

Reference in text with `@figure-main` or `@figure-main A`. See [MyST Figures Guide](https://mystmd.org/guide/figures).

### Building Outputs

MyST can build either a Remix app or static HTML:
- **`myst start`**: Runs the MyST app with hot reloading during development.
- **`myst build --html`**: Exports to static HTML without the Remix app. See [MyST deployment docs](https://mystmd.org/guide/deployment#creating-static-html) for details.

```bash
# HTML preview
myst build --html

# PDF export (requires Typst)
myst build --all
```

### Deployment

The `.github/workflows/deploy.yml` workflow automatically builds and deploys to GitHub Pages on push to `main`.

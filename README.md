# Book Summaries

## Generating PDFs

Requires [Pandoc](https://pandoc.org/) and a LaTeX distribution (e.g., BasicTeX):

```bash
brew install pandoc
brew install --cask basictex
```

Generate a PDF from a book's markdown files:

```bash
pandoc sre/chapter-*.md -o sre.pdf --toc --metadata title="Site Reliability Engineering - Book Summary"
```

# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This repository contains structured markdown summaries of technical books. Each book gets its own directory with one markdown file per chapter.

## Commands

### Generate PDF from book summaries
```bash
pandoc sre/chapter-*.md -o sre.pdf --toc --metadata title="Site Reliability Engineering - Book Summary"
```

### Generate PDF with note-taking margins
```bash
pandoc sre/chapter-*.md -o sre.pdf --toc \
  --metadata title="Site Reliability Engineering - Book Summary" \
  -V geometry:"left=1.5cm, right=9cm, top=2cm, bottom=2cm"
```

Requires Pandoc and a LaTeX distribution:
```bash
brew install pandoc
brew install --cask basictex
```

## Book Summarization Skill

When summarizing a new book:

1. Get the table of contents URL and extract chapter links using WebFetch
2. For each chapter, fetch HTML and generate a structured summary
3. Write each chapter to `{book-dir}/chapter-{NN}-{slug}.md`

### Chapter Summary Format

Each chapter summary must follow this structure:
- **Summary**: 2-3 sentence overview
- **Key Concepts**: 5-8 key terms with definitions
- **Section Summaries**: 2-3 sentences per major section
- **Practices**: Bulleted list of actionable recommendations
- **Key Takeaways**: 3-5 numbered takeaways with bold titles

### File Naming

Format: `chapter-{NN}-{slug}.md`
- `NN` = zero-padded chapter number (01, 02, ... 34)
- `slug` = lowercase, hyphenated chapter title

Examples: `chapter-01-introduction.md`, `chapter-06-monitoring-distributed-systems.md`

### Execution Options

- **Parallel subagents** (faster, higher cost): Launch one Task subagent per chapter
- **Sequential writes** (slower, lower cost): Fetch and write chapters directly from main agent

Note: Subagents may be blocked by project hooks; direct writes work more reliably.

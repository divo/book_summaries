# Book Summarization Skill

## Purpose
Summarize technical books (available as HTML pages) into structured markdown files, one per chapter.

## Usage

### Input
- A table of contents URL containing chapter links
- Target output directory

### Process
1. Extract all chapter URLs from the table of contents page using WebFetch
2. For each chapter:
   - Fetch the HTML content
   - Generate a structured summary
   - Write to output directory as `chapter-XX-slug.md`

### Execution Options

**Option A: Parallel Subagents (faster, higher cost)**
```
Launch one subagent per chapter using Task tool with subagent_type="general-purpose"
All agents run in parallel
```

**Option B: Direct Writes (slower, lower cost)**
```
Fetch and write chapters sequentially or in batches
```

Note: Subagents may be blocked by project hooks in "discussion mode". Direct writes from the main agent work more reliably.

## Output Format

Each chapter summary follows this structure:

```markdown
# Chapter N: Title

## Summary
[2-3 sentence overall summary of the chapter]

## Key Concepts
- **Term 1**: Definition or explanation
- **Term 2**: Definition or explanation
[5-8 key concepts introduced in the chapter]

## Section Summaries

### [Section Name]
[2-3 sentences summarizing this section]

### [Section Name]
[2-3 sentences summarizing this section]

[Continue for each major section...]

## Practices
- Actionable recommendation 1
- Actionable recommendation 2
[Bulleted list of recommended practices from the chapter]

## Key Takeaways
1. **Takeaway title**: Explanation
2. **Takeaway title**: Explanation
[3-5 main takeaways, numbered with bold titles]
```

## File Naming Convention

Format: `chapter-{NN}-{slug}.md`
- `NN` = zero-padded chapter number (01, 02, ... 34)
- `slug` = lowercase, hyphenated version of chapter title

Examples:
```
chapter-01-introduction.md
chapter-06-monitoring-distributed-systems.md
chapter-34-conclusion.md
```

## Example Source

This skill was developed to summarize the Google SRE Book:
- Source: https://sre.google/sre-book/table-of-contents/
- Output: 34 chapter summaries in `projects/observability/sre_summary/`

## Customization

Adjust the output format by modifying the prompt template:
- **More detail**: Request more sentences per section
- **Less detail**: Request bullet points only
- **Different focus**: Emphasize code examples, case studies, or specific themes

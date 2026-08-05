# WeChat Article Skill - Converting Technical Reports to Public Articles

Transform dry investment research reports into interesting and engaging WeChat articles for general readers.

## Features

- Remove technical details, maintain core points
- Add narrative and data visualization
- Targeted at general readers without financial knowledge background

## Design Philosophy

A good WeChat article must simultaneously satisfy three dimensions:
1. **Depth** — worthy of the time invested by readers (author's responsibility)
2. **Readability** — clear structure, good rhythm, non-discouraging (editor's responsibility)
3. **Actually understandable** — target readers won't give up midway (reader's responsibility)

Writing solo is easy to "please yourself" — the writer thinks it's clear, the reader doesn't understand. The essence of three-agent collaboration is **forcing introduction of external perspective**.

---

## Stage One: Research and Materials Collection

### Step One: Clarify Article Positioning

Before starting to write, confirm the following information (if user doesn't specify, ask proactively):

| Dimension | Confirmation Needed | Default Value |
|-----------|-------------------|---------------|
| **Target audience** | Technical background level | Some technical, but not domain expert |
| **Article depth** | Popularization/Medium depth/Very technical | Medium depth (with formulas but explained clearly) |
| **Article length** | Word count range | 3000-4000 words |
| **Need to download original materials?** | PDF/Images required | Yes |
| **Writing style** | Formal/Conversational/Direct | Conversational (like writing to smart friends) |

### Step Two: Deep Research

Use Agent tool to launch **in parallel** 2-3 Research Agents to collect sufficient materials:

**Research Agent A: Core Content Research**
- If paper interpretation: download PDF, extract core contributions, key figures, experimental results
- If technical topic: search latest developments, key papers, technical details
- If business/investment topic: search latest data, industry reports, competitive landscape

**Research Agent B: Industry Context and Application**
- Search for industry implementation of this technology/topic
- Which companies are using it? How is performance?
- Latest development trends and milestone events

**Research Agent C (Optional): Comparative Research**
- Comparison of similar methods/products
- Historical development trajectory
- Future evolution direction

### Step Three: Organize Materials Framework

After all Research Agents complete, organize:
1. **Core thesis** (summarize in one sentence the main message of the article)
2. **Key data** (3-5 most impactful data points)
3. **Image checklist** (which images needed, what are sources)
4. **Article outline** (6-8 section titles and core content)

---

## Stage Two: Author Agent Writes Initial Draft

Use Agent tool to launch **Author Agent** with detailed writing instructions.

### Author Agent Prompt Template

You are a deep technical writer responsible for writing a WeChat article.

## Target Audience
{Based on positioning confirmation from Step One}

## Writing Style Requirements
- Pure English expression, avoid mixed English-Chinese (technical terms in English on first appearance, then use English)
- Technical popularization for smart friends, not academic paper translation
- Use analogies to help understanding, but analogies should be appropriate, not clichéd
- Key formulas/data needed, but each requires plain language explanation
- Do not use emojis
- Paragraphs not exceeding 4 lines (WeChat reading environment)

## Core Content
{Organized materials, data, arguments}

## Article Structure Requirements
1. **Opening (first 3 paragraphs)**: Must have strong hook — open with data impact or counter-intuitive conclusion, not moderate analogy
2. **Background**: Why is this important? What problem does it solve?
3. **Core content (2-3 sections)**: Technical depth appears here, but each technical point needs "plain language translation"
4. **Evidence/Cases**: Use data and cases, don't speak abstractly
5. **Industry impact/Outlook**: What does this mean for the industry
6. **Conclusion**: A judgment with viral potential, suitable for being captured in screenshots

## Image Requirements
- Paper interpretation articles: MUST extract original images from PDF, insert directly into article using `![description](relative path)`, no `[Fig X: description]` placeholders
- Extraction method: use pdftoppm to render PDF pages as high-resolution PNG (at least 900 DPI), then use PIL to crop target chart areas
- Each image not less than 500KB, ensure high clarity
- Images uniformly stored in `assets/{topic_abbreviation}/` directory
- Non-paper articles: if images needed, search and download appropriate images, insert directly

## Formula Requirements
- All mathematical formulas use LaTeX format: inline with `$...$`, standalone formulas with `$$...$$`
- Forbidden to write formulas in plain text (like `> D_KL(P || Q) = ...`), MUST use LaTeX rendering format
- Each formula followed by "plain language translation"

Write complete initial draft, approximately {target word count} words.
# docx-forge

[![skills.sh](https://img.shields.io/badge/skills.sh-Jorgut/docx--forge-8A2BE2?style=flat-square)](https://skills.sh/Jorgut/docx-forge)
[![Install with npx](https://img.shields.io/badge/npx%20skills%20add-Jorgut%2Fdocx--forge-000?style=flat-square)](https://github.com/Jorgut/docx-forge)
![License](https://img.shields.io/github/license/Jorgut/docx-forge?style=flat-square)
![Agent Skill](https://img.shields.io/badge/Agent%20Skill-Document%20Engineering-2EA44F?style=flat-square)

**Professional Word document engineering — create, edit, and analyze .docx files.**

A comprehensive reference for generating Word documents programmatically, editing existing documents via XML, and mastering OOXML features like tracked changes, comments, tables, images, and multi-column layouts.

## Features

### Create
Generate .docx files with the `docx` (npm) library:
- Page setup (US Letter, A4, landscape)
- Table of contents
- Headers, footers, page numbers
- Tables with proper DXA-based sizing
- Bullet and numbered lists
- Images, hyperlinks, bookmarks
- Footnotes, tab stops, multi-column layouts
- 15+ critical gotchas documented from real-world usage

### Edit
Modify existing .docx files through XML:
- Unpack → edit XML → repack workflow
- Smart quotes for professional typography
- Full OOXML element reference

### Track Changes
Complete XML patterns for:
- Insertions and deletions
- Paragraph-level deletion marking
- Rejecting another author's changes
- Restoring deleted content
- Comments and threaded replies

## Quick Start

Install project dependencies in the repository you are working from. The npm package is named `docx`; this skill is named `docx-forge`.

```bash
npm install docx
```

Create a document:

```javascript
const { Document, Packer, Paragraph, TextRun } = require('docx');
const fs = require('fs');

const doc = new Document({
  sections: [{
    children: [
      new Paragraph({ text: "Hello, World!" }),
    ]
  }]
});

Packer.toBuffer(doc).then(buffer => {
  fs.writeFileSync("hello.docx", buffer);
});
```

Ask an agent to use the skill:

```text
Use docx-forge to create a client-ready Word proposal with tracked-change notes and a table of contents.
```

For an existing document:

```text
Use docx-forge to inspect this .docx, summarize its styles, and propose safe XML edits before changing anything.
```

## When to Use Which Approach

| You want to... | Use |
|---|---|
| Create a new document from scratch | `docx` (npm) library |
| Edit text in an existing document | Unpack → XML Edit → Repack |
| Review or accept tracked changes | `pandoc --track-changes=accept` |
| Extract content for analysis | `pandoc -t markdown` |
| Add complex tracked changes | Direct XML manipulation |
| Insert comments | XML comment markers |

## Dependencies

- **Node.js** — required for generation with the `docx` npm package
- **pandoc** — optional, useful for document reading and conversion
- **LibreOffice** — optional, useful for format bridging and PDF output
- **Poppler** — optional, useful for `pdftoppm` page rendering

## Verification

Before handing off a generated `.docx`, check:

- the file opens in Word or LibreOffice
- headings and lists use real Word structures, not plain styled text
- tables fit the page width
- tracked changes and comments appear under the intended author
- exported PDF pages match the expected pagination

## Install

```bash
npx skills add Jorgut/docx-forge
```

## License

MIT — feel free to use, modify, and distribute.

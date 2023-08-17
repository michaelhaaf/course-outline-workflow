---
author: Michael Haaf
title: Converting .docx to markdown and Back Again
date: August 17, 2023
---

## Overview

Document conversion workflow between Open Office XML (.docx) and Markdown (.md) and vice versa, applied to the 5A6-F22/23 course outline update in Fall 2023.

### the problem

- It is difficult to view course outline changes in Microsoft Teams
- Offline editing hard
- Complicated file format, vendor-lock-in 

### big picture solutions

- Content vs format
- Draft vs publication
- What file formats support our goals?
- What tools do we want to use?
- What frameworks are available for collaborative editting?

### a proposal

- Write course outline in any format (markdown or .docx)
- Convert proposal to markdown
- Propose changes in Pull Request
- Assess/evaluate changes in Pull Request comments
- Publish final course outline in PDF

### background reading

- ["Markdown: Syntax" by John Gruber](https://daringfireball.net/projects/markdown/syntax): A succinct overview of both the **how** and the **why** of Markdown.
- [CommonMark](https://commonmark.org/): Brief history and overview of Markdown, also a proposed specification of Markdown.

## Demonstration

Let's try this plan out!

### setup

There aren't many requirements:

#### pandoc

[pandoc](https://pandoc.org/) is the command line interface tool I've used throughout this workflow. 

> If you need to convert files from one markup format into another, pandoc is your swiss-army knife.

My notes in the following [sections](#demo) include the `pandoc` commands required to reproduce my workflow. 

You can find installation instructions for Mac/Windows/Linux on the [pandoc website](https://pandoc.org/installing.html)

The pandoc documentation a comprehensive set of [basic examples](https://pandoc.org/demos.html) which can be extended in an immense variety of ways by pandocs [template](), and [filter]() interfaces, as well as it's extensive default [CLI interface]().

#### possible alternatives

There are many. A short list:

- Dinguses
    - https://spec.commonmark.org/dingus/

### convert to md

```bash
> pandoc --standalone FALL2022.COMPUTERSCIENCE.420-5A6-AB.LARCOG.docx --output FALL2022.COMPUTERSCIENCE.420-5A6-AB.LARCOG.md
```

In this case, the `--standalone`, `--from`, and `--to` parameters are all inferred by the file extensions, allowing for the much more succinct: 

```bash
> pandoc FALL2022.COMPUTERSCIENCE.420-5A6-AB.LARCOG.docx -o FALL2022.COMPUTERSCIENCE.420-5A6-AB.LARCOG.md
```

### Convert back to docx

```bash
> pandoc FALL2022.COMPUTERSCIENCE.420-5A6-AB.LARCOG.md -o FALL2022.COMPUTERSCIENCE.420-5A6-AB.LARCOG-md-to-docx-no-ref.docx
> pandoc --reference-doc=FALL2022.COMPUTERSCIENCE.420-5A6-AB.LARCOG.docx FALL2022.COMPUTERSCIENCE.420-5A6-AB.LARCOG.md -o FALL2022.COMPUTERSCIENCE.420-5A6-AB.LARCOG-md-to-docx-no-ref.docx
```

# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a **Chinese-language computer networks learning notes repository** based on USTC (中科大) video lectures by 郑老师 and *Computer Networking: A Top-Down Approach* (7th Edition) by Kurose & Ross. The content is in Chinese with bilingual English terminology.

There is no build system, test suite, or CI — this is a pure documentation/content repository.

## Directory Structure

```
Chapter01_Computer_Networks_overview/   # Ch1: Internet & protocol layers
Chapter02_Application_Layer/            # Ch2: HTTP, DNS, P2P, CDN, Socket
Chapter03_Transport_Layer/              # Ch3: TCP, UDP, reliable transfer, congestion control
Chapter04_Network_Layer_data_plane /    # Ch4: IP, routers, forwarding, SDN data plane
Chapter05_Network_Layer_control_plane/  # Ch5: routing algorithms, OSPF, BGP, SDN control
Chapter06_Link_Layer/                   # Ch6: Ethernet, ARP, VLAN, MAC, error detection
Chapter08_Network_Security/             # Ch8: encryption, authentication, TLS, firewalls
```

Each chapter contains:
- `README.md` — chapter navigation with core/difficulty points per section
- `X.Y_*.md` — section-level notes following the standard template
- `images/` — referenced images named as `image.png`, `image1.png`, `image2.png`, …

Note: Chapter 7 (Wireless/Mobile) is not present in this repository.

## Note Format Convention

All section notes follow a strict template (defined in the root README's embedded prompt):

1. **Title**: `# 📘 X.Y Title (English Title)` with source attribution
2. **Overview**: `## 🧠 核心概念总览` — linked list of 10–15 knowledge points, preserving original source order
3. **Knowledge points**: `## ✅ 知识点N: Name` with anchor `idN`, each containing:
   - **理论** — theory in bullet lists
   - **注意点** — warnings (⚠️), tips (💡), cross-references (🔄), terminology (📋)
   - **教材示例/公式** — code blocks or LaTeX formulas where applicable
4. **Summary**: `## 🔑 核心要点总结` — 3-5 takeaway points
5. **Exam prep**: `## 📌 考试速记版` — key mechanisms, comparisons, common exam topics

Key conventions:
- **Bilingual terminology**: First occurrence of each term includes both Chinese and English, e.g. `传输层(Transport Layer)`
- **FSM descriptions**: Always use list format, never tables
- **Relative image paths**: `images/imageN.png` (referenced from the note file's location)
- **Cross-chapter links**: Chapter READMEs include next-chapter previews and return links to root

## Relevant Skills

This repo was built using these skills (available via `/skill-name`):
- **`course-notes-generator`** — generates individual section notes from PDFs/images/URLs. Used for creating `X.Y_*.md` files.
- **`chapter-nav-readme`** — generates per-chapter `README.md` navigation pages with core/difficulty points per section.
- **`course-root-readme`** — generates the root `README.md` with chapter navigation and the embedded note-generation prompt.

## Common Tasks

### Adding a new section note
1. Generate the note with `course-notes-generator` using source material (PDF/image/URL)
2. Place it in the correct chapter directory as `X.Y_Topic_Name.md`
3. Update the chapter `README.md` to include the new section in the navigation list
4. Update root `README.md` if adding a new chapter

### Adding a new chapter
1. Create the directory: `Chapter0X_Chapter_Name/`
2. Create `images/` subdirectory
3. Generate section notes and the chapter README
4. Add the chapter entry to root `README.md`

### Image paths
Images live in `ChapterXX_.../images/` and are referenced from notes as `images/imageN.png` (relative path from the `.md` file). When adding new images, follow the sequential naming convention `image.png`, `image1.png`, `image2.png`, …

## Source Materials

The primary sources for note content are:
- **Video course**: [中科大 计算机网络](https://www.bilibili.com/video/BV1JV411t7ow)
- **Textbook**: 《计算机网络：自顶向下方法》第7版 (Kurose & Ross)
- **Author website**: https://gaia.cs.umass.edu/kurose_ross/index.php

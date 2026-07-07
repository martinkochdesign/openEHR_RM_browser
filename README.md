# 🏥 openEHR Reference Model — Interactive Glossary Explorer

A lightweight, zero-dependency, single-page HTML application for browsing the [openEHR Reference Model](https://specifications.openehr.org/releases/RM/latest) class hierarchy interactively.

Built for clinical knowledge modellers, health informaticians, and developers working with openEHR who need a fast, offline-capable reference tool.

![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)
![No Dependencies](https://img.shields.io/badge/dependencies-none-brightgreen)
![Vanilla JS](https://img.shields.io/badge/built%20with-vanilla%20JS-yellow)

---

## ✨ Features

### Three-Panel Layout

| Left Panel | Center Panel | Right Panel |
|---|---|---|
| Searchable, filterable class list | Interactive attribute/function tree | Detail inspector for selected items |

### 🔍 Search & Filter
- **Full-text search** across class names, descriptions, attribute names, attribute descriptions, and data types
- **Type filters**: All · Class · Abstract · Interface · Enum
- Live result count

### 🌳 Interactive Tree
- **Inline expansion** — click ▶ on any attribute whose type is a known class to expand its structure recursively, without navigating away
- **Grouped sections** — own attributes first, then inherited (with "from `PARENT_CLASS`" labels); same for functions
- **Obligarity badges** — green `1..1` (mandatory), amber `0..1` (optional), with compact layout
- **Clickable data types** — navigate to any referenced class instantly
- **Inheritance breadcrumb** — full ancestor chain at the top of each class
- **Specializations** — child classes listed and clickable

### 🧭 Navigation
- **Back / Forward** with tooltip preview showing the target class name
- **Keyboard shortcuts**:
  - `↑` / `↓` — browse class list
  - `Enter` — select highlighted class
  - `Ctrl+K` or `/` — focus search
  - `Alt+←` / `Alt+→` — history back/forward

### 🎨 Appearance
- **☀️ Light / 🌙 Dark mode** — toggle in the header, preference saved to `localStorage`
- High-contrast text in both themes
- Sleek, modern CSS with custom scrollbars

### ⚙️ Extras
- **ƒ Functions toggle** — hide/show all functions to focus on data structure only
- **RM version** extracted automatically from source URLs and displayed in the header
- **Expand All / Collapse All** buttons
- **Stats bar** — total classes, abstract classes, interfaces
- **About dialog** — copyright, authorship, license info

---

## 🚀 Quick Start

```bash
git clone https://github.com/YOUR_USERNAME/openehr-rm-glossary.git
cd openehr-rm-glossary
```

Open `openehr_rm_glossary.html` in any modern browser. That's it — no build step, no server, no dependencies.

### File Structure

```
├── openehr_rm_glossary.html   # The application (HTML + CSS + JS)
├── glossary_data.js           # The data file (must be in the same folder)
├── README.md
└── LICENSE
```

> ⚠️ Both files must be in the **same directory**. The HTML loads the data via `<script src="glossary_data.js"></script>`.

---

## 📦 Data Format

`glossary_data.js` exposes three global constants:

```javascript
const glossary_extraction_date = "2026-07-06 08:34:46";

const glossary_extraction_source = [
  "https://specifications.openehr.org/releases/BASE/latest/base_types.html",
  "https://specifications.openehr.org/releases/RM/latest/common.html",
  // ...
];

const defined_classes = [
  {
    "class_name": "COMPOSITION",
    "description": "A composition is one ...",
    "type": "Class",
    "inherit": ["LOCATABLE"],
    "attributes": [
      {
        "attribute_name": "language",
        "existence": "1..1",
        "data_type": "CODE_PHRASE",
        "description": "Mandatory indicator of ..."
      }
      // ...
    ],
    "functions": [
      {
        "function_name": "is_persistent",
        "return_type": "Boolean",
        "description": "True if ...",
        "prerequisite": "..."
      }
      // ...
    ]
  }
  // ...
];
```

### Adding or Updating Classes

1. Edit `glossary_data.js` following the structure above
2. Update `glossary_extraction_date` with the current timestamp
3. Reload the HTML — changes appear instantly

---

## 🛠 Tech Stack

- **HTML5** — semantic markup
- **CSS3** — custom properties (variables) for theming, flexbox/grid layout
- **Vanilla JavaScript** — no frameworks, no build tools, no dependencies
- **localStorage** — theme preference persistence

Works fully offline once downloaded.

---

## 📄 License

This work is licensed under the Apache License, Version 2.0.

You are free to use, reproduce, modify, and distribute this work, in source or object form, for any purpose — including commercially — as long as you include a copy of the license and state any changes made. This license also grants an express patent license from contributors.

---

## 👤 Author

**Martin Andreas Koch, PhD**
Servei Català de la Salut (CatSalut)

---

## 🙏 Acknowledgements

- [openEHR Foundation](https://www.openehr.org/) — for the Reference Model specifications
- [openEHR Specifications](https://specifications.openehr.org/) — source of the class definitions


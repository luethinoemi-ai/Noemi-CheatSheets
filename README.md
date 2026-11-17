<div align="center">

# 📚 Noemi CheatSheets

**Personal knowledge base created during and after my apprenticeship.**

![Sphinx](https://img.shields.io/badge/Sphinx-Docs-ff69b4?style=for-the-badge&logo=sphinx&logoColor=white)
![Furo](https://img.shields.io/badge/Theme-Furo-8a2be2?style=for-the-badge)
![Markdown](https://img.shields.io/badge/Markdown-Notes-1f1f1f?style=for-the-badge&logo=markdown&logoColor=white)
![Status](https://img.shields.io/badge/Status-Growing-2ea44f?style=for-the-badge)

</div>

---

## 🎯 Purpose

This repository contains notes, cheat sheets, summaries and explanations of concepts learned during projects, school and work.
Everything is written short and clear, so I can find it again quickly.

> [!NOTE]
> This is a living project. New topics are added while I learn them.

---

## 🗂️ Topics

| | Topic | What's inside |
| :-: | :--- | :--- |
| 🐧 | **Operating Systems** | Linux basics, files, permissions, processes, search, navigation |
| 🌐 | **Networking** | DNS, HTTP, REST, JSON, WebSockets |
| 💻 | **Programming** | OOP, Git |
| 🧰 | **Tools** | DevTools, VS Code, KIS Web Simulator |
| 🕸️ | **Web Development** | HTML, CSS, JavaScript, DOM, Canvas, Vue.js |
| 📖 | **Glossary** | Short definitions of common IT terms |
| 📊 | **Business Analysis** | *Planned* |

### 🕸️ Web Development in Detail

| Area | Topics |
| :--- | :--- |
| **HTML** | Basics, elements, forms, semantic HTML, tables |
| **CSS** | Selectors, box model, flexbox, grid, responsive design |
| **JavaScript** | Variables, data types, functions, arrays, objects, classes, async/await |
| **DOM** | Selecting and creating elements, events |
| **Canvas** | Shapes, text, images, animations |
| **Vue.js** | Reactivity, components, templates, lifecycle hooks, watchers |

---

## 🚀 Getting Started

### 📥 1. Clone the repository

```bash
git clone https://github.com/luethinoemi-ai/Noemi-CheatSheets.git
cd Noemi-CheatSheets/docs
```

### 🔧 2. Install the requirements

```bash
pip install sphinx furo myst-parser
```

### 🏗️ 3. Build the documentation

```bash
make html
```

### 👀 4. Open it in the browser

```bash
xdg-open _build/html/index.html
```

> [!TIP]
> Install `sphinx-autobuild` and run `sphinx-autobuild . _build/html`.
> The page then reloads automatically every time you save a file.

---

## 📁 Project Structure

```text
Noemi-CheatSheets/
├── _alt/                  # old notes (archive)
├── docs/
│   ├── betriebssysteme/   # operating systems (Linux)
│   ├── netzwerk/          # networking
│   ├── programmierung/    # programming (OOP, Git)
│   ├── tools/             # tools
│   ├── web/               # HTML, CSS, JS, DOM, Canvas, Vue
│   ├── conf.py            # Sphinx configuration
│   ├── glossar.md         # glossary
│   ├── index.md           # start page
│   ├── Makefile
│   └── make.bat
└── README.md
```

---

## ✍️ Adding a New Cheat Sheet

1. Create a new `.md` file in the matching topic folder.
2. Add its name to the `toctree` in the `index.md` of that folder.
3. Run `make html` inside `docs` and check the result.
4. Commit and push your changes:

```bash
git add .
git commit -m "Add new cheat sheet"
git push
```

> [!IMPORTANT]
> One topic per sheet, clear headings, copy-paste-ready examples.

> [!WARNING]
> Always check commands before running them, especially anything with `sudo`.

---

## 🌱 Roadmap

- [x] Clean structure with Sphinx and the Furo theme
- [x] Linux, networking, web and Vue.js basics
- [ ] Add Business Analysis notes
- [ ] Publish the docs online with GitHub Pages
- [ ] Add more examples and diagrams

---

<div align="center">

Made with 💖 and a lot of coffee by **Nömi**

</div>

# Noemi CheatSheets

Personal knowledge base created during and after my apprenticeship as an application developer.

It contains notes, cheat sheets, summaries and explanations of concepts I learned in projects, at school and at work. The content is written with Sphinx and the Furo theme.

**Read online:** https://luethinoemi-ai.github.io/Noemi-CheatSheets/

## Topics

- **Operating Systems:** Linux basics, files, permissions, processes, search, navigation
- **Networking:** DNS, HTTP, REST, JSON, WebSockets
- **Programming:** OOP, Git
- **Tools:** DevTools, VS Code, KIS Web Simulator
- **Web Development:** HTML, CSS, JavaScript, DOM, Canvas, Vue.js
- **Glossary:** short definitions of common IT terms

Planned: Business Analysis.

## Build locally

You only need this if you want to work on the docs yourself.

```bash
git clone https://github.com/luethinoemi-ai/Noemi-CheatSheets.git
cd Noemi-CheatSheets/docs
pip install sphinx furo myst-parser
make html
```

The result is in `docs/_build/html/index.html`.

To reload the page automatically while editing:

```bash
pip install sphinx-autobuild
sphinx-autobuild . _build/html
```

## Project structure

```text
Noemi-CheatSheets/
├── _alt/                  old notes (archive)
├── docs/
│   ├── betriebssysteme/   operating systems
│   ├── netzwerk/          networking
│   ├── programmierung/    programming
│   ├── tools/             tools
│   ├── web/               HTML, CSS, JavaScript, DOM, Canvas, Vue.js
│   ├── conf.py            Sphinx configuration
│   ├── glossar.md         glossary
│   └── index.md           start page
└── README.md
```

## Adding a cheat sheet

1. Create a new `.md` file in the matching topic folder.
2. Add it to the `toctree` in the `index.md` of that folder.
3. Run `make html` in `docs` and check the result.
4. Commit and push. The website is rebuilt automatically.

## Author

Noemi, application development apprentice.
GitHub: [@luethinoemi-ai](https://github.com/luethinoemi-ai)

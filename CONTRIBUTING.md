# Contributing to AI CEO OS

First off, thank you for considering contributing! AI CEO OS is a community project and every contribution matters.

## Ways to Contribute

### 🐛 Report bugs
Open an issue using the **Bug Report** template. Include:
- What you did
- What you expected to happen
- What actually happened
- Browser and OS

### 💡 Suggest features
Open an issue using the **Feature Request** template. The best feature requests explain the problem they solve, not just the solution.

### 🌍 Add a language
AI CEO OS supports EN and FR. Adding a new language is one of the most impactful contributions.

1. Open `src/index.html`
2. Find the `T` object (the translation dictionary)
3. Add a new language key (e.g. `es`, `de`, `pt`)
4. Translate all keys — including the Claude prompts
5. Add the language button to the `lang-switcher` in the HTML
6. Submit a PR with the title `feat: add [language] support`

### 🎨 Improve the UI
The UI is built in vanilla HTML/CSS/JS inside a single file. No build step needed. Open `src/index.html` in a browser and edit away.

### 🧠 Improve prompts
The quality of the system lives or dies by its prompts. If you have experience with prompt engineering, improving the strategy, CEO, agent, or output prompts is extremely valuable.

Prompts are in the `T` object under keys like `stratSys`, `stratUser`, `ceoSys`, `ceoUser`, etc.

### 📖 Improve documentation
Fix typos, add examples, improve clarity. Documentation PRs are always welcome.

---

## Getting Started

```bash
# 1. Fork the repository on GitHub

# 2. Clone your fork
git clone https://github.com/YOUR_USERNAME/ai-ceo-os.git
cd ai-ceo-os

# 3. Create a branch
git checkout -b feat/your-feature-name

# 4. Make your changes
# The entire app is in src/index.html

# 5. Test in your browser
open src/index.html

# 6. Commit with a clear message
git commit -m "feat: add Spanish language support"

# 7. Push and open a PR
git push origin feat/your-feature-name
```

---

## Commit Convention

We use conventional commits:

| Prefix | When to use |
|---|---|
| `feat:` | New feature |
| `fix:` | Bug fix |
| `docs:` | Documentation only |
| `style:` | Formatting, no logic change |
| `refactor:` | Code restructuring |
| `i18n:` | Adding or fixing translations |
| `prompt:` | Improving Claude prompts |

---

## Code Style

- The project is intentionally a **single HTML file** — keep it that way for v1.x
- No build tools, no npm, no bundler — it should run by opening a file
- Use CSS variables from the design system for all colors
- Keep JavaScript clean and readable — no minification in source
- Add a comment when doing something non-obvious

---

## PR Review Process

1. Open a PR with a clear title and description
2. A maintainer will review within a few days
3. Address any feedback
4. Once approved, it gets merged

---

## Code of Conduct

Be kind. Be constructive. Help others. That's it.

---

Thank you for making AI CEO OS better! 🙏

# Copilot Instructions

## Build, test, and lint commands

- `npm install` installs the Slidev/Vue dependencies.
- `npm run dev` starts the Slidev dev server for `slides.md` and opens the presentation locally.
- `npm run build` produces the static presentation in `dist/`.
- `npm run export` runs Slidev's export pipeline for the deck.
- There are no repository-defined test or lint scripts in `package.json`, so there is no native full-suite or single-test command to run.

## High-level architecture

- This repository is a Slidev presentation, not a conventional Vue application. `slides.md` is the active entrypoint for the keynote, and its top-level frontmatter defines the deck-wide defaults such as the `apple-basic` theme, dark color schema, Shiki highlighting, and `mdc: true`.
- Most of the presentation is authored directly in `slides.md` as Slidev markdown separated by `---` frontmatter blocks. Slides can freely mix markdown with inline HTML/Vue markup; the current deck uses that heavily for layout and inline SVG logo blocks.
- `components/` is for Vue components that Slidev can use inside markdown slides. `snippets/` is for reusable code fragments that can be embedded into slides with Slidev snippet imports such as `<<< @/snippets/...`.
- `pages/` is where split-out slide fragments would live when using Slidev's `src:` imports. The current keynote is primarily single-file; `pages/imported-slides.md` is starter-template reference material rather than part of the live deck.
- Deployment is static. Both `netlify.toml` and `vercel.json` build with `npm run build`, serve `dist/`, and rewrite routes to `index.html`. Netlify pins Node `20`.

## Key conventions

- Treat `slides.md` as the source of truth for the real presentation. `default-slides.md` is the stock Slidev starter/reference deck and should not be used as the main place for keynote edits.
- Prefer deck-level frontmatter in `slides.md` for shared defaults, then add per-slide overrides with new `---` blocks instead of repeating configuration inline.
- Follow the existing authoring style of keeping slide-specific layout in markdown with inline HTML and UnoCSS utility classes instead of creating separate styling files for one-off presentation tweaks.
- The current deck favors embedded SVG/HTML for logos and visual composition directly in slide content. Match that style when updating neighboring slides unless there is a clear reason to extract shared assets or components.
- If you add interactive or reusable UI, put it in `components/` and consume it from markdown. If you add reusable code examples, put them in `snippets/` and embed them into slides instead of duplicating long fenced blocks.

---

## Conventional Commits

All commits MUST follow the Conventional Commits specification:

```
<type>(optional scope): <short summary>
```

### Allowed Types

- `feat` — new content, feature, or page
- `fix` — corrections (typos, broken links, config issues)
- `docs` — documentation-only changes
- `style` — formatting, whitespace, no content change
- `refactor` — restructuring without changing output
- `perf` — performance improvements
- `build` — build system or dependency changes
- `ci` — CI/CD changes
- `chore` — maintenance tasks

### Scope (Optional)

Use scope when helpful:

- `content`
- `layout`
- `theme`
- `config`
- `assets`
- `docs`
- `ci`
- `seo`

Example:

```
feat(content): add article on static site performance
```

---

## Commit Message Style (50/72 Rule)

### Structure

```
<type>(scope): <subject line>

<body>
```

### Subject Line

- Max **50 characters**
- Imperative mood ("add", not "added")
- No trailing period
- Be specific and concise

### Body

- Wrap at **72 characters**
- Explain _why_, not just _what_
- Use full sentences and paragraphs
- Write for humans, not machines
- Include context, tradeoffs, and intent when useful

---

## Example Commit

```
feat(content): add guide on Hugo image optimization

This introduces a new guide explaining how to optimize images
in Hugo using built-in processing features. It focuses on
practical examples and avoids external tooling to keep the
workflow simple.

The goal is to improve page load performance while keeping
the authoring experience straightforward for contributors.
```

---

## What to Avoid

- One-line commits with no context (unless trivial)
- Vague messages like "update stuff" or "fix things"
- Overly long subject lines
- Mixing unrelated changes in a single commit
- Auto-generated or machine-style commit messages

---

## Pull Request Expectations

- Keep PRs focused and small
- Include a clear description of changes
- Reference related issues if applicable
- Ensure the site builds successfully
- Preview changes locally before submitting
- Verify GitHub Pages and custom-domain changes carefully when touching the
  deployment workflow or `CNAME`

---

## Agent-Specific Instructions

- Always infer appropriate commit type and scope
- Rewrite commit messages to match this standard if needed
- Prefer multiple small commits over one large commit
- When generating content, ensure it matches existing tone and structure
- Do not introduce breaking structural changes without explicit instruction

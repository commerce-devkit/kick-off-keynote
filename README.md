# Commerce DevKit kickoff keynote

This repository contains the Slidev deck for the Commerce DevKit
kickoff keynote. The active presentation lives in `slides.md` and is
built as a static site for local review and deployment.

## Commands

- `npm install` installs the Slidev dependencies.
- `npm run dev` starts the deck locally at
  `http://localhost:3030`.
- `npm run build` creates the production-ready output in `dist/`.
- `npm run export` runs Slidev's export pipeline.

## Repository layout

- `slides.md` is the source of truth for the keynote.
- `components/` holds reusable Vue components for slides when needed.
- `snippets/` stores reusable embedded code examples.
- `pages/` is available if the deck is later split into imported slide
  fragments.
- `dist/` contains the generated static presentation.

## Deployment

Both Netlify and Vercel are configured to build the deck with
`npm run build` and serve the generated `dist/` output as a static
single-page app.

## Notes

This repository started from the Slidev starter template, but the
starter deck is no longer the project entrypoint. Update `slides.md`
for presentation changes and treat any helper files as secondary
reference material only.

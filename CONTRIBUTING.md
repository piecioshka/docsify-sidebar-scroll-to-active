# Contributing

How the plugin works and how to work on it. For installation and usage, see the [README](README.md).

## Getting started

Prerequisites: Node.js in the version from `.nvmrc` (`lts/krypton`). The plugin has no dependencies and no build step, so there is nothing to install: the published file is `index.js` as it is in the repository.

## Project structure

- `index.js` - the whole plugin; it registers itself in `window.$docsify.plugins`.
- `demo/` - a Docsify site with 40 chapters, long enough for the sidebar to scroll.
- `CHANGELOG.md` - release notes in the [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) format.

## How it works

```js
hook.ready(() => requestAnimationFrame(scrollSidebarToActive));
```

- Runs on Docsify's `ready` event (first render complete).
- Defers to the next animation frame so layout numbers are stable.
- Computes the offset by walking `offsetParent` chain up to the sidebar, which is more reliable than `offsetTop` alone when the active item sits inside nested `<ul>` blocks with their own positioning context.

## Running the demo

`demo/index.html` loads the plugin from `../index.js` and the sidebar from `/demo/_sidebar.md`, so serve the repository root with any static file server and open `/demo/`. Docsify itself comes from unpkg.

There are no automated tests, lint or format scripts; check changes in the demo by opening a chapter far down the list and reloading the page.

## Releases

The package is published to npm as `docsify-sidebar-scroll-to-active`. The `files` field in `package.json` ships only `index.js`, `CHANGELOG.md` and `LICENSE`. For a new version, add an entry to `CHANGELOG.md` and bump `version` in `package.json` (Semantic Versioning).

## Conventions

Commits follow Conventional Commits (`chore: add MIT license`).

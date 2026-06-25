# docsify-sidebar-scroll-to-active

[![node version](https://img.shields.io/node/v/docsify-sidebar-scroll-to-active.svg)](https://www.npmjs.com/package/docsify-sidebar-scroll-to-active)
[![npm version](https://badge.fury.io/js/docsify-sidebar-scroll-to-active.svg)](https://badge.fury.io/js/docsify-sidebar-scroll-to-active)
[![downloads count](https://img.shields.io/npm/dt/docsify-sidebar-scroll-to-active.svg)](https://www.npmjs.com/package/docsify-sidebar-scroll-to-active)
[![size](https://packagephobia.com/badge?p=docsify-sidebar-scroll-to-active)](https://packagephobia.com/result?p=docsify-sidebar-scroll-to-active)
[![license](https://img.shields.io/npm/l/docsify-sidebar-scroll-to-active.svg)](https://piecioshka.mit-license.org)

🔨 A tiny [Docsify](https://docsify.js.org/) plugin that scrolls the sidebar to
the currently active item on page load — so users always see "you are here"
without having to scan the menu.

Zero dependencies, ~50 lines of code.

## Installation

### Via CDN (recommended)

Add **after** `docsify.min.js` in your `index.html`:

```html
<script src="https://unpkg.com/docsify-sidebar-scroll-to-active/index.js"></script>
```

Pin a version for reproducible builds:

```html
<script src="https://unpkg.com/docsify-sidebar-scroll-to-active@1.0.0/index.js"></script>
```

[jsDelivr](https://www.jsdelivr.com/) works too:
`https://cdn.jsdelivr.net/npm/docsify-sidebar-scroll-to-active@1.0.0/index.js`

### Via npm

```bash
npm install docsify-sidebar-scroll-to-active
```

## Usage

No configuration. Drop the tag in — the plugin registers itself with Docsify
via `window.$docsify.plugins` and runs on the `ready` hook.

The plugin looks for:

- `aside.sidebar` — the Docsify sidebar container
- `li.active > a` (preferred) or `li.active` — the currently active item

If both are present, the sidebar's `scrollTop` is set so the active item is
vertically centered within the visible sidebar area.

If either is missing, the plugin does nothing.

## How it works

```js
hook.ready(() => requestAnimationFrame(scrollSidebarToActive));
```

- Runs on Docsify's `ready` event (first render complete).
- Defers to the next animation frame so layout numbers are stable.
- Computes the offset by walking `offsetParent` chain up to the sidebar,
  which is more reliable than `offsetTop` alone when the active item sits
  inside nested `<ul>` blocks with their own positioning context.

## License

[The MIT License](https://piecioshka.mit-license.org) @ 2026

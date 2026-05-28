# docsify-sidebar-scroll-to-active — demo

This is a tiny demo Docsify site for the [`docsify-sidebar-scroll-to-active`](https://github.com/piecioshka/docsify-sidebar-scroll-to-active) plugin.

The sidebar on the left has 40 chapters. **Click "Chapter 20 — open this one"**
(roughly in the middle of the list) and reload the page. You'll see the sidebar
scroll itself so Chapter 20 stays visible — without the plugin, you'd have to
hunt for the active item every refresh.

The chapter pages here are intentionally empty — the goal is just to show what
the plugin does to the sidebar.

## How it's wired up

```html
<script src="https://unpkg.com/docsify/lib/docsify.min.js"></script>
<script src="../index.js"></script>
```

That's it. The plugin self-registers via `window.$docsify.plugins` and runs on
the `ready` hook.

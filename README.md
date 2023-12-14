# Minimal reproducible example

This project represents a small example that shows an issue with Sveltekits default behaviour regarding `trailingSlash` introduced in Sveltekit version 1.30.1. The corresponding [docs](https://kit.svelte.dev/docs/page-options#trailingslash) state that Sveltekit removes trailing Slashes by default which does not really work consistently anymore.

## Setup

- `trailingSlash` not specified
- `paths.base` default value

## Repro using the sample app

1. Clicking the Foo link on the root page will redirect to `http://localhost:5173/home/foo/` and the trailing shlash does not get removed. Reloading on this page will lead to removal of the trailing slash as follows `http://localhost:5173/home/foo`. This is some inconsistency since I would expect consistent behaviour accross reloads.
2. Having the trailing slash like `http://localhost:5173/home/foo/` will cause an issue when using a link where the `href` only specifies the child like `href="bar"` since it will try to navigate to the non existing route `http://localhost:5173/home/foo/bar`. This feature works with Sveltekit removing trailing slashes

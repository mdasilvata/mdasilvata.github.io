# Cookie echo test page

A one-file page that prints the cookies the browser sent to it. Use it to check whether cookies you set or preload for a site hosted on a shared platform domain (here, `github.io`) actually reach that site.

## Live page

https://mdasilvata.github.io/

## What it does

On load, `index.html` runs one line of JavaScript that replaces the page body with:

    COOKIES: <document.cookie>

`document.cookie` lists the cookies the browser has for this page's host. If none apply, you see `COOKIES: ` with nothing after it. Cookies marked `HttpOnly` are not listed.

## How to use it

1. Set a cookie for the host `mdasilvata.github.io` in your test browser or tool. For example, name `test_cookie`, value `1`, path `/`.
2. Open the page.
3. Read the line it prints:
   - `COOKIES: test_cookie=1` means the cookie reached the site.
   - `COOKIES: ` means it did not.
4. Capture the result however your tool allows, for example the page source or a screenshot.

## Why a github.io page

`github.io` is a public suffix: every user's `<name>.github.io` is a separate site under a shared parent domain. Browsers refuse cookies scoped to the whole suffix, and they silently store a cookie set for `.github.io` as host-only on `github.io` itself. A cookie meant for `mdasilvata.github.io` has to be scoped to that host. This page makes the difference visible.

## Notes

- The page is static and public. It stores nothing, sends nothing anywhere, and never reads cookies from other sites.
- Don't put real secrets in a test cookie. Anyone who can see your capture can see the value.
- Delete the repo when you no longer need it.

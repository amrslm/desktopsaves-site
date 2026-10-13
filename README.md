# desktopsaves-site

The page behind Desktop's shared-folder links, on **desktopsaves.com**.
Static HTML on GitHub Pages: no framework, no build step.

Desktop's Share Folder makes links like `https://desktopsaves.com/f/#<id>.<key>`.
Everything after `#` stays in the browser, so GitHub Pages never sees which
share is being opened. If the app is installed, iOS opens the link in
Desktop (via the association file); otherwise `f/share.js` fetches the
encrypted folder from the Supabase `share` function and decrypts it in the
tab with WebCrypto. The server holds ciphertext only. Add `?dev` before the
`#` to read from the dev Supabase project.

```
CNAME                                          desktopsaves.com (apex)
.nojekyll                                      serve the files as-is
.well-known/apple-app-site-association         universal links: /f/* opens in the app
robots.txt                                     crawling allowed, indexing refused (noindex on every page)
index.html, 404.html                           intentionally blank
f/index.html                  /f/              shared-folder viewer
f/share.js, f/share.css                        the viewer's script and styles
f/og.jpg, f/wordmark.png                       link-preview image, footer wordmark
```

The app's Privacy Policy and Support pages stay on arkive.tech
(`~/Projects/vrkive-site`), which App Store Connect points at.

## DNS (Squarespace Domains)

Apex A records to GitHub Pages: `185.199.108.153`, `185.199.109.153`,
`185.199.110.153`, `185.199.111.153`; `www` CNAME to `amrslm.github.io`.

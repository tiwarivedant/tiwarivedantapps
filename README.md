# tiwarivedantapps

Support and privacy pages for Vedant Tiwari's iPhone apps, served by GitHub Pages at
<https://tiwarivedant.github.io/tiwarivedantapps/>.

| App      | Support URL (App Store Connect)                            | Privacy Policy URL (App Store Connect)                             |
| -------- | ---------------------------------------------------------- | ------------------------------------------------------------------ |
| myWallet | https://tiwarivedant.github.io/tiwarivedantapps/mywallet/ | https://tiwarivedant.github.io/tiwarivedantapps/mywallet/privacy/ |
| myHome   | https://tiwarivedant.github.io/tiwarivedantapps/myhome/   | https://tiwarivedant.github.io/tiwarivedantapps/myhome/privacy/   |

## How the site works

- Plain hand-written HTML plus one shared stylesheet, `assets/site.css`. No build step, no framework, no JavaScript.
- No external requests of any kind: no analytics, cookies, fonts, CDNs or embeds. The privacy pages say so, and the site has to keep that promise.
- `.nojekyll` makes GitHub Pages serve the files as they are.
- Each app has one lowercase folder with an `index.html` (Support) and a `privacy/index.html` (Privacy Policy), so URLs end in `/`.
- Each app's accent colours are CSS variables in `site.css`, switched on by a class on `<body>`, for example `<body class="app-mywallet">`.
- `404.html` uses absolute `/tiwarivedantapps/...` links because GitHub Pages serves it at whatever path was missing.
- Publishing: GitHub Pages deploys from the `main` branch, `/` (root). Pushing to `main` updates the site.

## Adding another app

1. Copy `mywallet/` to a new lowercase folder, for example `myvoyage/`.
2. Add the app's icon to `assets/icons/` (`sips -Z 512 AppIcon-1024.png --out assets/icons/myvoyage.png`) and add its accent tokens (`.app-myvoyage { … }`, light and dark) to `site.css`. Update the `<body>` class, icon paths, titles and meta descriptions in the copied pages.
3. Re-check every privacy statement against **that app's own code**: network calls, iCloud/CloudKit, analytics or crash reporting, third-party SDKs, location, photos, contacts, camera, and anything else it touches. Never copy myWallet's claims to another app.
4. Add the app's card to `index.html`.
5. Once the URLs are submitted to Apple, never move or rename the folder.

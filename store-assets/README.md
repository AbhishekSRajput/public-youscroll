# Chrome Web Store assets

Source material for the YouScroll store listing. **Nothing in this directory
is bundled into the extension** — the build copies only `public/` and the
compiled sources into `dist/`.

`listing-copy.md` is the canonical public copy: name, summary, description,
single-purpose statement, permission justifications, data disclosures, and
reviewer notes. `SEO.md` records why that copy is worded the way it is and
what to measure to find out whether it worked.

## What is here

| File                            | Field it fills                                     |
| ------------------------------- | -------------------------------------------------- |
| `listing-copy.md`               | Every text field in the store console              |
| `SEO.md`                        | Strategy and the measurements to take              |
| `release-metadata.json`         | The URLs the console asks for, in one place        |
| `../public/icons/icon-128.png`  | Chrome store icon (128x128, generated)             |
| `store-logo-300x300.png`        | Edge Add-ons "Extension logo" (300x300)            |
| `small-promo-440x280.png`       | Small promotional tile (required)                  |
| `large-promo-1400x560.png`      | Marquee promotional tile (optional, for featuring) |
| `screenshot-01.png` … `-05.png` | Screenshots, 1280x800                              |

The `.svg` files beside the promo PNGs are the editable originals. Edit those,
then re-render; do not hand-edit the PNGs.

## Regenerating

```sh
npm run build              # screenshots run against dist/, so build first
npm run store:screenshots  # screenshot-01..05.png
npm run store:promos       # promo tiles, from their SVG sources
npm run store:logo         # store-logo-300x300.png
npm run icons              # ../public/icons, including the 128 store icon
```

The three `store:*` generation commands drive a headless Chromium over the
DevTools protocol, the same approach `verify:selectors` uses and with the same
`BROWSER_BIN` override if no browser is found at the usual paths. Add
`--headful` to `store:screenshots` to watch it happen.

## The screenshots are real, and the page they are on is ours

The captures are of the actual built extension: `capture-screenshots.mjs`
serves `dist/` over localhost and loads the real content-script bundle as a
module. A page-local, in-memory adapter supplies the Chrome storage calls needed
to exercise Saved GIFs without touching a browser profile. The same runtime,
modules, import pipeline, effects, and selector registry that ship in the
extension produce every interface in the captures. None of these images is a
mockup drawn to look like the product.

What they are _not_ captured on is youtube.com, and that is deliberate. Every
asset in a listing has to be material we own. A capture of a real watch page
would put another company's trademarks — and strangers' video titles, avatars,
and comment text — into promotional artwork. `CONTRIBUTING.md` rules that out,
and it is the kind of thing listings get pulled over.

So `scripts/lib/demo-watch-page.mjs` is a page this repo owns: an invented site
("Nimbus"), an invented video, invented commenters. Its _structure_ is not
invented — every element the selector registry names is present and arranged
the way YouTube arranges it, which is what lets the real module mount on it.

Two consequences worth knowing:

- If `npm run verify:selectors` starts failing because YouTube moved something,
  this fixture needs the same update `selectors.json` does. The capture script
  fails loudly rather than silently producing a screenshot with no panel in it.
- If you would rather ship captures of the real site, take them yourself and
  make your own call on the trademark question. Do not point this script at
  youtube.com.

## The listing links to a different repository

This repository is private, so nothing in the store listing may link into it —
a privacy-policy URL that 404s for a reviewer is a common rejection. The
listing points instead at `AbhishekSRajput/public-youscroll`. Its public
documents live in `docs/public-docs/` in this source repository and are copied
to the public repository root.

Publishing it means copying four documents and this directory:

```text
docs/public-docs/README.md               -> README.md
docs/public-docs/PRIVACY.md              -> PRIVACY.md
docs/public-docs/ISSUES.md               -> ISSUES.md
docs/public-docs/THIRD_PARTY_NOTICES.md  -> THIRD_PARTY_NOTICES.md
LICENSE                                  -> LICENSE
store-assets/                            -> store-assets/
```

`store-assets/` has to come along because the public README embeds
`store-assets/large-promo-1400x560.png` at the top. Keep the source repository
and the public one in step: a privacy policy that describes a build you no
longer ship is worse than none.

## Before submitting

- [ ] The description in `listing-copy.md` names only features on `main`.
      Nothing from an unmerged branch.
- [ ] The walkthrough and reviewer test steps in `listing-copy.md` match
      `DEFAULT_SETTINGS` in `src/lib/settings.ts` — in particular which tab the
      panel opens on. A settings default is a one-line change that silently
      invalidates the copy and the screenshots.
- [ ] The name in `listing-copy.md` matches `NAME` in `manifest.config.ts`.
      Chrome takes the listing name from the package, not the console.
- [ ] The public docs repository exists, is public, has Issues enabled, and
      every URL in `release-metadata.json` resolves from a signed-out browser.
- [ ] `docs/public-docs/PRIVACY.md` describes the build being submitted, and
      its effective date and version line are current.
- [ ] `docs/public-docs/THIRD_PARTY_NOTICES.md` matches what the build
      actually bundles. Re-check it after any dependency change.
- [ ] Screenshots were regenerated after the last UI change.
- [ ] The version in `manifest.config.ts` (via `package.json`) is the one you
      mean to publish.

Keep proof of authorship for every listing asset. Everything in this directory
is generated from sources in this repository by the scripts listed above.

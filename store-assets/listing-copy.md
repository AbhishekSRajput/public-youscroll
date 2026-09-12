# YouScroll store listing copy

Canonical public listing copy for the Chrome Web Store and, if YouScroll is
submitted there, Microsoft Edge Add-ons. Keep this file in sync with the
packaged manifest (`manifest.config.ts`), the live store console, and
`PRIVACY.md`.

The title and summary stay plain and descriptive. The public description uses
one relevant emoji per section or feature to make a long listing easier to scan;
do not turn them into decorative runs or repeat them for search visibility.

Two constraints this copy is written against, both from the Chrome Web Store
Listing Requirements policy:

- **No keyword repeated unnaturally more than five times**, no bare lists of
  sites or brands, no unattributed testimonials, and no claim the extension
  does not actually deliver. See the keyword budget at the end.
- **Nothing here may describe a feature the shipped build does not have.** A
  description that contradicts the extension's behavior is grounds for removal
  on its own. Keep the panel, pop-out player and Video playground details in
  sync with the build that is submitted.

## Extension name

    YouScroll — Scroll Comments & Up Next Independently

51 of the 75 characters Chrome allows. Chrome takes the listing name from the
packaged manifest, so this string lives in `manifest.config.ts` and cannot be
edited in the store console alone.

The brand leads so brand search resolves. "Scroll Comments & Up Next
Independently" names both panes and the shared benefit instead of presenting
Up Next as a secondary destination. The platform term moves to the summary,
where the listing still makes the YouTube context explicit.

## Store summary / manifest short description

    Scroll YouTube comments and Up Next independently beside the video without
    moving the page. App-like YouTube, one feature at a time.

132 of the 132 characters allowed. This is the meta description the store and
search engines surface, and it is the only body text many people read.

The first sentence is the whole product in one line and uses the words a
person would search with. The second says what kind of thing this is: small
and deliberate rather than a suite. Do not rewrite it into a feature list;
the field is too short to hold one and the description below already does it.

## Description

✨ Scroll Comments and Up Next without losing the video.

YouScroll turns the YouTube watch page into a more useful space. Comments and
recommendations share a full-height, tabbed panel beside the player and scroll
independently. Open Play for local drawing, GIF, throwing and face-effect tools
layered over the current video.

🎬 HOW IT WORKS

1. Install it and open a watch page.
2. The right-hand column is now a full-height panel with two tabs: Comments
   and Up Next. Scroll either one without moving the player.
3. Click Play to open the Video playground. It starts on Doodle, followed by
   GIFs, Throw and Faces.
4. Draw, place a GIF, throw an effect or choose a face sticker. Close the
   playground at any time to return normal video input.
5. Use the toolbar popup to switch features on or off and choose which
   right-column pane opens first.

🧰 CORE FEATURES

- 📌 Independent panel: Comments and Up Next are one click apart. Each pane has
  its own scroll, and more comments keep loading as you reach the bottom.

- 🎨 Doodle first: Play opens directly to a pen and eraser with six colors,
  adjustable size, Undo and Clear all.

- 🎞️ GIF overlays: import a local GIF, drag it over the video and change its size.
  Up to four GIFs can play together. YouScroll tries a lossless optimization on
  your device and uses it only when it is smaller; pixels, resolution, frames,
  timing and transparency stay unchanged. An already optimized file is kept as
  it is.

- 💾 Saved GIFs: reusable files stay in this browser's local extension storage.
  The shelf holds up to 12 files and 6 MiB of encoded GIF data. A valid GIF that
  does not fit still works on the current video; it simply is not added to the
  shelf. Imports support up to 64 MiB and 8 million pixels per frame, preserve
  the original resolution within those practical limits, and have no frame
  count or duration cutoff.

- 🍅 Eight throwables: fling tomatoes, eggs, slime, confetti, flowers, hearts,
  stars or snowballs. Flight arcs, squash and particle bursts respect the
  browser's reduced-motion preference.

- 😎 Face effects: local landmark tracking follows position and rotation. Choose
  a moustache, horns, hair, hero mask, pirate patch, Laser Eyes with a red
  charging glow, or a Super Saiyan power-up with the same red eye glow and a
  golden body aura. You can also import a local PNG, JPEG or WebP face image
  with size and placement controls.

- 🪟 Pop-out player: the control-bar button opens the current video in the
  browser's Picture-in-Picture window.

- ↔️ Mode-aware layout: the panel steps aside in theater mode, fullscreen, live
  chat and narrow windows. The Play button remains available in the player
  controls where supported.

- ⚡ Instant, reversible controls: toolbar toggles apply to open tabs without a
  reload. Switching a feature off or navigating away returns the borrowed page
  elements to their original places.

🙌 WHO IT IS FOR

Anyone who reads YouTube comments while the video is still playing: people
following a tutorial, people watching a talk and reading the discussion beside
it, and anyone who wants lightweight effects without uploading their media.

💡 WHAT PEOPLE USE IT FOR

- Reading the comments on a tutorial without losing sight of the step.
- Keeping the recommendations one click away instead of buried.
- Drawing a quick note or reaction over a playing video.
- Reusing a favorite GIF without uploading it to a service.
- Adding animated throws or face-following effects for fun.
- Watching in a floating window while working in another application.

🔒 PRIVACY

YouScroll has no account, no server, and no analytics. It makes no network
requests in this build and contains no remote code. Granted site access is
limited to www.youtube.com.

Settings use Chrome sync. GIFs you explicitly import may be saved in local
extension storage on this browser; they never sync or upload. Doodles,
on-screen placements and imported face images stay in tab memory.

Face tracking starts only after you choose a face sticker. It temporarily
samples video pixels on your device with a detector bundled in the extension.
Frames and face geometry are not saved or transmitted, and the feature does
not recognize identity. Profiles, occlusion, quick cuts and videos that block
pixel reads can interrupt tracking.

No comment text, video title, channel name or watch history is read, logged or
transmitted. See the privacy policy for the complete local-processing and
storage details.

## Single purpose description

YouScroll's single purpose is to improve the YouTube watch-page viewing
workspace while the current video stays visible. It gives Comments and Up
Next their own scrolling panes, provides a Picture-in-Picture button, and adds
an optional Video playground for local visual effects over that video.

The playground starts on Doodle and also supports local GIF overlays, eight
animated throws and face-following stickers. Its face detector, model and
effects are packaged with the extension. User-selected GIF files may be kept
in local extension storage for reuse; all other artwork and placements remain
temporary.

YouScroll does not read or transmit comment text, titles, channel names or
watch history. Face stickers temporarily process sampled video pixels on the
device only after the user selects one. Every page mutation is reversible and
is undone when its feature is switched off or the user navigates away.

## Permission justifications

### storage

Required for two local-first functions:

- `chrome.storage.sync` holds one small settings object containing feature
  toggles and the preferred starting tab. The popup writes it and open YouTube
  tabs read it so changes take effect immediately.
- `chrome.storage.local` holds GIF files the user explicitly imports and that
  fit the Saved GIFs library. Stored records contain GIF bytes, byte length, a
  format version and a content hash used to avoid duplicates.

Saved GIFs stay on the current browser profile and do not sync. No filename,
video identifier, placement, comment, title, channel name or watch history is
written to storage.

### Host permission (https://www.youtube.com/*)

YouScroll's content script needs to run on YouTube watch pages because that
is where the elements it rearranges and the video it decorates live. It reads
the positions of the comments and recommendations containers to move them
into a panel and restore them later. It also adds extension-owned controls and
can draw effects on an extension-owned canvas over the player.

When the user chooses a face sticker, the content script temporarily samples
the current video's pixels for local landmark detection. Those pixels and the
resulting geometry stay on the device, are not persisted and are released when
tracking stops.

The scope is a single host and cannot widen by accident: the build fails if
any host pattern in the manifest escapes `https://www.youtube.com`. YouScroll
requests no `tabs`, `scripting`, `webRequest`, `history`, `cookies`, or
`<all_urls>` permission.

### Optional host permission (http://localhost/*)

The packaged manifest retains one optional localhost permission for the
deferred Watch Together prototype. This build does not register that module,
show a control for it, request the permission or connect to a relay. It is not
granted during installation and none of the available features use it.

## Remote code

Select "No, I am not using remote code."

YouScroll's content script and popup are bundled into the extension package at
build time. The face tracker includes its JavaScript, model files and
WebAssembly in the package. It uses no remotely fetched script, model or other
executable code and has no background service worker.

## Data usage disclosures

YouScroll does not collect or transmit user data. Settings, user-selected GIF
files and temporary video-frame processing stay under the local storage and
processing rules above. Nothing is sent to the developer, an analytics
provider or an advertiser; the available features make no network requests.

In the store's privacy form:

- Do not select any data-collection category. The extension transmits no data
  off the device.
- Certify that data is not sold, not used for advertising, not used for
  purposes unrelated to the single purpose, and not used to determine
  creditworthiness or for lending.
- Declare the privacy policy URL below. It is required whenever any user data
  is handled at all, including settings.

One thing to state accurately rather than round off: settings are stored in
`chrome.storage.sync`, so if the user is signed into Chrome, that object
travels through Google's own sync service between the user's own browsers,
exactly as any other extension setting does. It contains no identifiers and
nothing about what the user watches, and it never reaches the developer.

Saved GIF files use `chrome.storage.local`, do not pass through Chrome sync and
remain on the browser profile where they were imported. Sampled face-tracking
frames and imported face images are transient and are never written to either
storage area.

## Search terms (Edge Add-ons: max 7 terms, 30 characters each)

Chrome has no keyword field, so these apply only if YouScroll is also
submitted to Edge. Ordered by how directly each matches what the extension
does, since Edge weights earlier terms more heavily.

1. scroll youtube comments
2. youtube video effects
3. gif video overlay
4. doodle on youtube
5. face stickers
6. picture in picture
7. youtube sidebar

## Keyword budget

The store treats unnatural repetition of a keyword more than five times as
listing-metadata spam, which gets an item rejected rather than merely ranked
lower. Counts below are for the public copy on this page (name, summary, and
description) and should be re-checked after any edit.

| Target phrase   | Cap | Placement                         |
| --------------- | --- | --------------------------------- |
| scroll comments | 3   | name and description              |
| up next         | 5   | name, summary and description     |
| youtube         | 5   | summary and natural body mentions |

"comments", "video", "panel", and "page" are core nouns this product cannot
be described without, and repeating them is description rather than
manipulation. Keep them natural and do not pad.

Deliberately absent, and they must stay absent:

- Names of competing extensions, or any third-party product other than the
  platform the extension works on.
- Testimonials or review quotes. Unattributed testimonials in a description
  are an explicit policy violation.
- "Best", "#1", "top rated", or any claim not verifiable from the listing.
- Any feature the shipped build does not have. In particular, the public name,
  summary and description must not advertise Watch Together, a GIF recorder,
  a now-playing bar, audio-only mode or any other unavailable interface.

## URLs

These point at the **public docs repository**, not at the source repository.
`AbhishekSRajput/youscroll` holds the extension's source and is private, so a
reviewer following a link into it would get a 404 — which is one of the most
common causes of a rejected review. The public repository is published from
`docs/public-docs/` in the source repo; see the README there.

- Homepage: https://github.com/AbhishekSRajput/public-youscroll
- Privacy policy:
  https://github.com/AbhishekSRajput/public-youscroll/blob/main/PRIVACY.md
- Support:
  https://github.com/AbhishekSRajput/public-youscroll/blob/main/ISSUES.md

Confirm each resolves publicly from a signed-out browser before submitting.

## Notes to reviewer

YouScroll requires no account and has no developer-operated server, analytics,
telemetry, advertising or remote code. The packaged face model and WebAssembly
run locally. The optional localhost host permission belongs to a deferred
Watch Together prototype; this build never requests or uses it.

HOW TO TEST

1. Open any YouTube watch page on a window wider than about 1020 pixels.
2. Confirm the right-hand column is a full-height panel with two tabs,
   Comments and Up Next. On a fresh install it opens on Up Next, which is the
   default; the recommendations appear in the panel rather than beside it.
3. Click the Comments tab. Confirm the comments appear in the same panel and
   that the player does not move when the panel is scrolled.
4. Scroll the panel to the bottom twice and confirm more comments load each
   time. This is YouTube's own lazy loading working inside the panel.
5. Click Play beside the panel tabs. Confirm the playground opens in Doodle,
   draw over the video, then use Undo and Clear all.
6. Open GIFs and import a local `.gif`. Confirm it plays at its original aspect
   ratio, can be dragged and resized, and appears in Saved GIFs after the page
   reloads. Clear all should remove the placed copy but keep the saved file;
   its delete button removes the saved file.
7. Open Throw and click the video after choosing an item. Confirm it flies to
   the pointer and plays an impact animation.
8. On a video with a clear human face, open Faces and choose Laser Eyes. Confirm
   a localized red charging glow follows both eyes without projected beams.
   Super Saiyan adds the same red eye glow and a golden aura below the face.
9. Press "t" for theater mode and then fullscreen. The panel steps aside in
   both and the Play entry moves to the player controls. Exit and confirm the
   panel and artwork return.
10. Click the pop-out button at the left of the player's right-hand controls.
    The browser's Picture-in-Picture window opens with the same video.
11. Open the toolbar popup, set the starting tab to Comments, and reload the
    watch page. It now opens on Comments.
12. Switch each available feature off from the popup with the tab still open.
    Each reverts immediately without a reload.
13. Open a live stream with chat. Confirm the panel steps aside and the Play
    button remains available in the player controls.
14. Open a non-watch page such as the YouTube home page and confirm nothing is
    injected.

BUILD FROM SOURCE

Requirements: Node.js 22.x and npm. From the source archive root:

1. `npm ci`
2. `npm run build`

The unpacked extension is written to `dist/`. No global build tools are
needed. The submitted package is produced by this process.

# YouScroll Privacy Policy

- **Effective date:** September 13, 2026
- **Applies to:** YouScroll 1.0.0 and later
- **Extension operator:** Sagrid, operated by Abhishek Singh
- **Privacy and support contact:** <codecube99@gmail.com>

YouScroll is a local-first Chrome extension that rearranges the YouTube watch
page and can draw user-selected effects over its video. This policy describes
the data the extension handles, why it handles it, where it is stored and the
choices available to users.

In this policy, "YouScroll," "we," and "us" refer to the extension operator
identified above.

## Summary

- YouScroll does not require an account or sign-in.
- YouScroll has no developer-operated data server, analytics, advertising,
  tracking or telemetry.
- The available features make no network requests. All executable code, face
  models and WebAssembly are included in the extension package.
- Feature settings are stored in `chrome.storage.sync`. GIFs the user chooses
  may be stored separately in `chrome.storage.local` for reuse on that browser
  profile. They are never uploaded or synced.
- Doodles, throws, on-screen placements, imported face images, sampled video
  frames and face geometry remain in temporary tab memory.
- YouScroll does not read, store, transmit or log comment text, video titles,
  channel names, search queries or watch history.
- Face tracking starts only after a face sticker is selected. It temporarily
  processes sampled video pixels on the device and does not recognize identity.
- Granted site access is limited to `https://www.youtube.com/*`. One optional
  localhost permission remains for an unavailable prototype and is not
  requested or used by this build.
- Extension controls are part of the ordinary page, so scripts on that page can
  see them just as they can see other page elements.

## Data YouScroll handles

| Data                                   | How it is used and retained                                                                                                                                              |
| -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Feature settings                       | On/off states and the preferred starting pane let the extension remember the user's choices. Stored in Chrome sync.                                                      |
| Saved GIF files                        | GIF bytes explicitly selected by the user, plus byte length, a format version and a content hash for duplicate detection. Stored locally only when the library has room. |
| Positions of page elements             | Read in memory so the comments and recommendations containers can be moved, sized and restored. Not stored.                                                              |
| Drawing and placement input            | Pointer coordinates, selected effects and placement controls render artwork over the current video. Kept in tab memory only.                                             |
| Current video identifier               | Used temporarily to prevent artwork from carrying onto a different video. Not persisted or assembled into watch history.                                                 |
| Imported face image                    | A PNG, JPEG or WebP chosen by the user is decoded for a custom sticker. Kept in tab memory only.                                                                         |
| Sampled video pixels and face geometry | Processed locally after a face sticker is selected so effects can follow a face. Temporary and not stored or transmitted.                                                |

These are the complete categories handled by the available features.

YouScroll does not read or store comment text, comment counts, video titles,
channel names, descriptions, search queries, watch history, form entries,
passwords, authentication cookies, financial information, health information
or personal communications. It does not build an activity log.

Scroll, resize, keyboard and pointer events are handled only as they occur so
the interface can respond, resize and undo artwork. They are not logged or
transmitted. YouTube's own loading and activity handling continue independently
of the extension.

## Where data is stored

### Settings in Chrome sync

One versioned settings object is stored in `chrome.storage.sync`. It contains
feature toggles and the preferred Comments or Up Next starting pane. The schema
also retains a display-name field from the deferred Watch Together prototype;
version 1.0.0 has no interface that uses or transmits it.

If the user is signed into Chrome, Google may sync this object between that
user's own browsers, as it does other extension settings. It contains no user
identifier and nothing about what the user watches, and the extension operator
receives no copy. Google's handling of Chrome sync is covered by
[Google's privacy policy](https://policies.google.com/privacy).

If the user is not signed into Chrome, the settings remain in that browser
profile.

### Saved GIFs in local extension storage

GIFs explicitly imported by the user are saved in `chrome.storage.local` when
the Saved GIFs library has room. YouScroll first tries to optimize the GIF
losslessly on the device. It saves the smaller result when one is produced and
keeps the original bytes when the file is already optimized or no smaller
lossless result is available.

The library stores the selected GIF bytes, byte length, a format version and a
SHA-256 content hash used only to avoid duplicates. It does not store the
filename, video identifier, screen position or watch history. Saved files stay
on the current browser profile, do not pass through Chrome sync and are never
uploaded.

The library accepts up to 12 files and 6 MiB of encoded GIF data. A valid GIF
that exceeds the library limit or cannot be saved still plays on the current
video; the interface reports that it is available for that video only.

### Temporary tab memory

On-screen artwork, decoded GIF frames, GIF placements, imported face images,
sampled video frames and face geometry remain in tab memory. The current video
identifier is used only to scope that artwork to one video. None of this state
is written to Chrome storage.

Artwork survives layout changes for the same video. Clear all, navigation,
disabling the playground or closing the tab releases it. Clear all does not
delete Saved GIF files; each saved file has its own delete control. Deleting a
saved source does not remove a copy already placed on the current video.

## Video playground processing

### Doodles and throws

Doodles and animated throws are drawn on extension-owned canvases over the
video. The video element is not replaced, downloaded or recorded. Coordinates
and appearance remain in memory so the artwork can be redrawn after a resize
and removed with Undo or Clear all.

### GIF import and optimization

GIF import accepts files up to 64 MiB and 8 Mi pixels per frame, including
3840 by 2160. It has no 160-frame or 30-second animation cutoff. Local lossless
optimization preserves pixels, dimensions, frames, delays and transparency;
the original is retained when optimization does not make it smaller.

Playback decodes frames on demand at their original dimensions and retains a
bounded frame cache instead of the complete decoded animation. Compressed input
and temporary decoder working memory remain on the device. Up to four GIFs can
be placed at once.

### Face images and tracking

The Faces tab accepts local PNG, JPEG and WebP images up to 4 MiB and no
larger than 4096 by 4096 pixels. The image is decoded to a bounded bitmap for a
custom sticker. It is not uploaded, logged or saved in the GIF library.

Selecting a face sticker starts local detection with a bundled MediaPipe Face
Landmarker and a bundled JavaScript pico detector as fallback. Models,
JavaScript and WebAssembly ship inside the extension and are not downloaded at
runtime. A detached canvas samples the current video at most 10 times per
second, with a maximum side of 480 pixels. A private message channel transfers
a temporary pixel copy to a worker in an extension-owned frame.

Sampled JavaScript pixel buffers are cleared after processing. Normalized face
rectangles, rotation, eye and facial landmarks, and short-lived continuity ids
support stable placement between samples. The ids do not identify a person;
YouScroll performs no face recognition, biometric-template creation or
identity matching.

Laser Eyes and the pirate patch use temporary eye landmarks. Super Saiyan uses
the same localized red eye glow and draws a golden aura around an estimated
torso below the detected face. It does not scan or segment the person's body.

Tracking pauses when the tab is hidden or the video is paused and resets after
seeking or changing the video. Removing face stickers, clearing artwork or
disabling the playground stops tracking and releases its buffers. There is no
camera or microphone access, image upload, persistent frame storage or face
geometry transmission. If a video prevents pixel reads, tracking stops and the
extension does not bypass the browser restriction; doodles, GIFs and throws
remain available.

## Visibility to the page

YouScroll moves YouTube's comments and recommendations containers into its
right-column panel and adds controls and canvases to the page. These are
ordinary elements in the page's DOM. Scripts running on that page, including
YouTube's own scripts, can see the added elements and the changed layout, as
they can see the rest of the page.

The content script runs in Chrome's isolated world. Face inference runs in an
extension-owned frame and worker; only a private `MessagePort` receives the
temporary frame copy.

## Permissions and why they exist

| Permission                  | Why it is needed                                                                                                                                                     |
| --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `storage`                   | Saves the synced settings object and device-local Saved GIF library described above. It also lets open tabs react immediately to setting and library changes.        |
| `https://www.youtube.com/*` | Lets the content script run on watch pages, rearrange the layout, add controls and overlays, and process video pixels locally after the user selects a face sticker. |

The manifest also contains one optional `http://localhost/*` permission for
the deferred Watch Together prototype. Version 1.0.0 does not register that
module, expose a control, request the permission or connect to a relay. The
permission is not granted during installation and the available features do
not use it.

YouScroll requests no `tabs`, `scripting`, `webRequest`, `history`, `cookies`,
`clipboardRead` or `<all_urls>` permission. It has no background service worker.
The build fails if any granted host pattern escapes `www.youtube.com`, or if
the optional list contains anything except the single retained relay origin.

## How data is used

Settings activate the features and starting pane the user selected. Saved GIF
files support the reusable local shelf. Temporary drawing, placement and face
data render the visible effects the user requested. None is used to profile the
user, measure usage, advertise, determine creditworthiness or serve an
unrelated purpose.

## Sharing and disclosure

YouScroll does not sell, rent, share or transfer user data. Nothing handled by
the available features is sent to the extension operator, an analytics
provider, an advertiser or a data broker.

The operator may disclose information if required by law, but holds no
server-side copy of settings, files, frames, page content or activity and
therefore has none of that data to disclose.

## Retention and deletion

Settings remain in Chrome's extension storage until the user changes them,
clears extension data, resets the browser profile or uninstalls YouScroll.
Saved GIFs remain until the user deletes each file, clears extension data,
resets the browser profile or uninstalls the extension. Chrome removes local
extension storage on uninstall.

Temporary playground data follows the shorter lifecycle described above.
Switching a feature off immediately reverts its page changes in tabs that are
already open.

Because there is no server-side copy, the extension operator cannot retrieve,
export, correct or delete local extension data on a user's behalf. The user
controls it through the extension and Chrome.

## Security

YouScroll packages its executable code, model and WebAssembly with the
extension and loads no remote code. Available features make no network
requests, so their data has no extension-operated transmission path. Stored
data remains subject to the security of Chrome, the browser profile, the
operating system and the device.

The controls and canvases are deliberately rendered into the current page and
are visible to page scripts as described under **Visibility to the page**.

## External services and links

YouScroll contacts no external service in version 1.0.0. Its store listing
links to this policy and the support page; opening one is an ordinary browser
navigation governed by the operator of that site.

YouTube continues to load, render and log activity exactly as it would without
the extension, including loading more comments as the user scrolls. Google's
handling of that activity is covered by
[Google's privacy policy](https://policies.google.com/privacy).

The Chrome Web Store and Chrome browser may separately process installation,
update, diagnostic or store activity under Google's policies. That processing
is not performed by YouScroll.

## Children

YouScroll is a watch-page layout and local video-effects utility. It is not
directed to children under 13, or under the minimum age required by local law,
and does not knowingly request or collect personal information from children.
The same local processing and storage practices apply to every user.

## Chrome Web Store Limited Use

YouScroll's use of information received from Google APIs adheres to the Chrome
Web Store User Data Policy, including the Limited Use requirements. It limits
data use to providing the disclosed single purpose and does not use or transfer
user data for personalized advertising, unrelated purposes, creditworthiness
or lending decisions.

## Changes to this policy

If YouScroll's data practices change, this policy, the Chrome Web Store privacy
disclosures and any required in-product disclosure will be updated before the
changed practice begins. Material changes will carry a new effective date and
extension version.

## Contact

Questions, privacy requests and security reports should be sent to:

<codecube99@gmail.com>

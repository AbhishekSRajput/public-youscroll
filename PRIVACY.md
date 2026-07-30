# YouScroll Privacy Policy

- **Effective date:** July 31, 2026
- **Applies to:** YouScroll 0.4.0 and later
- **Extension operator:** Sagrid, operated by Abhishek Singh
- **Privacy and support contact:** <codecube99@gmail.com>

YouScroll is a local-first Chrome extension that rearranges the YouTube watch
page so the comments can be read beside the video instead of below it. This
policy describes the data the extension handles, why it handles it, where it
is stored, and the choices available to users.

In this policy, "YouScroll," "we," and "us" refer to the extension operator
identified above.

## Summary

- YouScroll does not require an account and has no sign-in.
- YouScroll has no developer-operated data server, analytics, advertising,
  tracking, or telemetry.
- YouScroll makes no network requests of its own and contains no remote code.
- The only thing YouScroll stores is a small settings object: which features
  are switched on and which tab the panel opens on.
- YouScroll does not store, transmit, or log page content. It does not record
  which videos you watch, what the comments say, or where you have been.
- YouScroll runs on `https://www.youtube.com` and has access to no other site.
- The panel YouScroll builds is part of the ordinary page, so scripts on that
  page can see it, as they can see the rest of the page.

## Data YouScroll handles

| Data                                | How it is used                                                                                                                                                                                                   |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Feature settings                    | Two on/off switches, one per feature, so the extension does what you last asked it to. Stored.                                                                                                                   |
| Default tab preference              | Whether the panel opens on Comments or Up Next. Stored.                                                                                                                                                          |
| Positions of YouTube's own elements | Read in memory while a feature is active, so the comments and recommendations containers can be moved into the panel and returned to their exact original position when the feature is switched off. Not stored. |
| The comment count shown on the page | Read as text to label the panel's tab, on the same page it was read from. Not stored, and never sent anywhere.                                                                                                   |

That is the complete list.

YouScroll does not read or store the text of comments, video titles, channel
names, descriptions, search queries, watch history, form entries, passwords,
authentication cookies, financial information, health information, or personal
communications. It does not build an activity log. It observes scroll position
and window size only to keep the panel the right height and to let YouTube's
own lazy loading keep working inside it, and it retains neither.

Nothing YouScroll handles is transmitted to the extension operator, to an
analytics provider, to an advertiser, or to a data broker. There is no server
on the other end of any request, because YouScroll makes none.

## Where data is stored

The settings object is stored under a single key in `chrome.storage.sync`,
Chrome's own extension storage.

One consequence is worth stating plainly rather than rounding off: if you are
signed into Chrome, `chrome.storage.sync` means that object travels through
Google's sync service between your own browsers, exactly as any other
extension setting does. It contains no identifiers and nothing about what you
watch — it is a pair of on/off switches and a tab preference — and it never
reaches the extension operator. Google's handling of Chrome sync is covered by
[Google's privacy policy](https://policies.google.com/privacy), not this one.

If you are not signed into Chrome, the settings stay on the device.

## Visibility to the page

YouScroll works by moving YouTube's own comments and recommendations
containers into a panel it adds to the page, and by adding one button to the
player's control bar. Those elements are ordinary parts of the page's DOM.

This means scripts running on that page, including YouTube's own, can see the
elements YouScroll adds and the fact that it has rearranged the layout. That
is inherent to changing a page you are looking at rather than a choice about
your data: YouScroll passes no information to those scripts, and the content it
moves was already on the page and already visible to them.

YouScroll runs in Chrome's isolated content-script world and does not expose
an API, a global variable, or a message channel that page scripts can call.

## Permissions and why they exist

| Permission                  | Why it is needed                                                                                                                   |
| --------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| `storage`                   | Saves the settings object described above, and lets an open YouTube tab notice immediately when you change a setting in the popup. |
| `https://www.youtube.com/*` | Lets the content script run on YouTube watch pages, which is where the elements it rearranges are.                                 |

YouScroll requests no `tabs`, `scripting`, `webRequest`, `history`, `cookies`,
`clipboardRead`, or `<all_urls>` permission, and no optional permissions. It
has no background service worker.

The host scope is enforced by the build, which fails if any host pattern in
the manifest escapes `https://www.youtube.com`. The narrow scope is the whole
privacy argument, so it is checked mechanically rather than by review.

## How data is used

The settings object is used for one thing: deciding which features are active
and how the panel opens. It is not used to profile you, is not combined with
anything else, and is not used for any purpose other than the extension's
disclosed single purpose.

## Sharing and disclosure

YouScroll does not sell, rent, share, or transfer user data to anyone. There
is no data to transfer: nothing leaves your browser as a result of using the
extension.

The operator may disclose information if required by law, but holds no
server-side copy of anything and therefore has nothing about you to disclose.

## Retention and deletion

Settings remain in Chrome's extension storage until you change them, clear the
extension's data, reset the browser profile, or uninstall the extension.
Chrome removes the stored settings when YouScroll is uninstalled.

Switching a feature off in the popup immediately reverts the page and stops
the extension from acting on it, in tabs that are already open, without a
reload.

Because there is no server-side copy, the extension operator cannot retrieve,
export, correct, or delete your local extension data on your behalf. You have
direct and complete control over it through Chrome.

## Security

YouScroll packages all of its executable code with the extension and executes
no remotely hosted code. It makes no network requests, so there is no
transmission to intercept. The data it stores is a pair of booleans and a
string, and it is subject to Chrome, browser-profile, operating-system, and
device security controls.

The panel YouScroll builds is deliberately rendered into the current page and
is not isolated from scripts on that page, as described under **Visibility to
the page**.

## External services and links

YouScroll contacts no external service. The extension's store listing links to
this policy and to its support page; if you open one, the operator of that
site processes the visit under its own policy.

YouTube continues to load, render, and log your activity exactly as it would
without the extension, including loading further pages of comments as you
scroll, which is YouTube's own code doing its own work inside the panel.
Google's handling of that activity is covered by
[Google's privacy policy](https://policies.google.com/privacy).

The Chrome Web Store and the Chrome browser may separately process
installation, update, diagnostic, or store activity under Google's policies.
That processing is not performed by YouScroll.

## Children

YouScroll is a layout utility for the YouTube watch page. It is not directed
to children under 13, or under the minimum age required by local law, and it
does not knowingly request or collect personal information from children. It
collects nothing from anyone, regardless of age.

## Chrome Web Store Limited Use

YouScroll's use of information received from Google APIs adheres to the Chrome
Web Store User Data Policy, including the Limited Use requirements. YouScroll
limits its use of user data to providing its disclosed single purpose and does
not use or transfer user data for personalized advertising, for unrelated
purposes, or for creditworthiness or lending decisions.

## Changes to this policy

If YouScroll's data practices change, this policy, the Chrome Web Store
privacy disclosures, and any required in-product disclosure will be updated
before the changed practice begins. Any change that widened data handling
would require a manifest permission change, which Chrome shows you at install
or update time. The effective date at the top identifies the current version.

## Contact

Questions, privacy requests, and security reports should be sent to:

<codecube99@gmail.com>

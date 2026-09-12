# YouScroll store search strategy

Why the copy in `listing-copy.md` is worded the way it is, and what to measure
to find out whether it worked.

**This file contains no measurements yet.** Ranking arguments made from
invented numbers are worse than no argument, so the tables below are left
empty with the method for filling them. Fill them before the first release and
again 90 days after, and the conclusions in this file become checkable.

## What the listing is competing for

YouScroll solves one specific irritation: browsing Comments or Up Next should
not move the video. YouTube's comments live below the player, and its
recommendations share the page scroll. People who look for a fix search in
roughly three shapes:

1. **The symptom.** "youtube comments while watching", "read comments without
   scrolling", "scroll up next without page moving". Low volume individually,
   very high intent, and almost nobody writes listing copy in these words.
2. **The mechanism.** "scroll youtube comments", "youtube comments sidebar",
   "pinned comments". Medium volume, medium intent, and the terms most likely
   to be typed into the store's own search box.
3. **The category.** "youtube layout", "youtube tweaks", "youtube enhancer".
   High volume, low intent, and dominated by large multi-feature extensions
   that a new focused extension will not displace.

The listing targets 2 and 1, in that order, and deliberately does not chase 3.

The reasoning: shape 3 is where established extensions with six-figure user
counts live, and their advantage there is popularity, which is not a field
this copy controls. Shape 2 is winnable because it is specific, and shape 1
converts best because someone typing the symptom has already decided they want
exactly this. A listing that ranks tenth for a category term and first for
"comments side panel" gets more installs than the reverse.

## Where the terms are placed, and why

The name is the heaviest relevance field a listing controls, and Chrome takes
it from the packaged manifest rather than the store console. So "Scroll
Comments" and "Up Next" are in the name, while the summary supplies the
platform term and symptom phrasing ("beside the video", "without moving the
page").

The description opener repeats the symptom in a full sentence, because the
opener is what the store truncates into search results and what a person
actually reads before deciding to scroll.

What is **not** in the name: "YouTube", "sidebar", "side panel", and
"pop-out". The summary immediately establishes the platform; the middle two
describe the layout but not its benefit; and the last is a secondary feature.
Keeping them out leaves the title focused on the extension's main scrolling
behavior.

## The honest limits of copy

Chrome's own curation documentation describes ranking as a blend of relevance,
quality and editorial value, and popularity, where popularity means install
count and rating volume. Copy moves relevance. It does not move the other two.

So the realistic sequence for a new listing with no users is:

1. **Now.** Win the long tail. Nobody is writing copy for "read youtube
   comments without losing the video". These queries are small and they
   convert.
2. **After the first 25 or so ratings.** Contend on the mechanism terms, where
   relevance can outweigh a modest popularity gap.
3. **Category terms.** Requires featured placement or a user base in the
   thousands. Treat it as a 6-12 month objective, not a copy-edit outcome.

Anyone promising a top-five slot on a category term from a description rewrite
is selling something.

## The non-copy levers, in order of effect

These matter more than word choice and are worth more attention than this
file's word count implies.

1. **Screenshots.** The first screenshot is the single highest-leverage asset
   in the listing: it is shown at the top of the detail page and in some
   search surfaces, and it decides whether the description gets read at all.
   `screenshot-01.png` is therefore the plainest statement of the value, with
   a caption that reads at thumbnail size.
2. **Ratings.** Rating count and recency feed popularity directly. The
   cheapest honest source is a working extension and a support link that gets
   answered.
3. **A verified publisher domain.** Chrome shows a verified badge for
   publishers who prove a domain. It costs a DNS record and is one of the few
   trust signals available to a new listing.
4. **Release cadence.** "Last updated" is visible on the listing, and a
   selector fix shipped promptly after YouTube changes its markup is both a
   ranking signal and the thing that keeps the extension working at all.
5. **The homepage and privacy policy URLs.** A dead privacy-policy link is a
   common rejection cause, and a real homepage is a trust signal.

## What to measure

Record these before the first release and again after 90 days. Search from a
signed-out browser, since a signed-in session personalizes results.

### In-store position

| Query                           | Position at launch | +90 days |
| ------------------------------- | ------------------ | -------- |
| pinned comments                 |                    |          |
| youtube comments sidebar        |                    |          |
| comments side panel             |                    |          |
| youtube comments while watching |                    |          |
| youtube layout                  |                    |          |

### The competitive baseline

Fill this from the live listings on the day you measure. It is here to keep
expectations calibrated, not to copy anything from those listings.

| Extension | Users | Rating (count) | Featured | Verified domain | Last update |
| --------- | ----- | -------------- | -------- | --------------- | ----------- |
|           |       |                |          |                 |             |

### Listing conversion

From the Chrome Web Store developer dashboard, once there is traffic:

| Metric                       | At launch | +90 days |
| ---------------------------- | --------- | -------- |
| Impressions                  |           |          |
| Detail-page views            |           |          |
| Installs                     |           |          |
| Installs / detail-page views |           |          |

If impressions rise but the install rate does not, the problem is the
screenshots or the summary, not the keywords. If impressions stay flat, the
problem is relevance or popularity. That split is the reason to track both.

## Rules this listing will not break to rank better

- No competitor names, and no lists of sites or brands.
- No testimonials, invented or real-but-unattributed.
- No superlatives that cannot be checked from the listing itself.
- No feature named in the listing that the shipped build does not have. This
  is the one that is easy to break by accident: if a module is written but not
  merged to `main`, it does not go in the copy.
- No keyword repeated past the budget in `listing-copy.md`.

The first four are policy violations that get an item removed rather than
demoted. The fifth is the same. None of them is worth a ranking position.

# Third-Party Notices

YouScroll includes software developed by third parties. This document covers
the production packages and build-generated runtime/CSS included in the
distributed browser extension built from the committed lockfile. Build-time
and test-only tools that emit no distributed code — TypeScript, ESLint,
Prettier, Vitest, PostCSS, and their dependencies — are not listed.

The settings popup bundles its React UI dependencies. The content script
bundles `gifenc` for local GIF optimization and an adapted pico face-detector
fallback. An extension-owned worker bundles MediaPipe and its local model and
WebAssembly runtime. Nothing is downloaded at runtime.

## Bundled runtime packages

| Package                 | Version | Distributed contribution            | License    | Source                                                            |
| ----------------------- | ------- | ----------------------------------- | ---------- | ----------------------------------------------------------------- |
| React                   | 18.3.1  | Settings popup UI                   | MIT        | https://github.com/facebook/react/tree/v18.3.1/packages/react     |
| React DOM               | 18.3.1  | Settings popup rendering            | MIT        | https://github.com/facebook/react/tree/v18.3.1/packages/react-dom |
| @radix-ui/react-slot    | 1.3.3   | Popup component composition         | MIT        | https://github.com/radix-ui/primitives                            |
| @radix-ui/react-switch  | 1.3.7   | Accessible toggle in the popup      | MIT        | https://github.com/radix-ui/primitives                            |
| clsx                    | 2.1.1   | Conditional class names             | MIT        | https://github.com/lukeed/clsx/tree/v2.1.1                        |
| tailwind-merge          | 2.6.1   | Tailwind class deduplication        | MIT        | https://github.com/dcastil/tailwind-merge/tree/v2.6.1             |
| lucide-react            | 0.462.0 | Popup icon                          | ISC        | https://github.com/lucide-icons/lucide                            |
| gifenc                  | 1.0.3   | Local lossless GIF re-encoding      | MIT        | https://github.com/mattdesl/gifenc                                |
| @mediapipe/tasks-vision | 0.10.32 | Local face-landmark worker and WASM | Apache-2.0 | https://github.com/google-ai-edge/mediapipe                       |

`@radix-ui/react-switch` brings with it the Radix primitives it is built from
— `@radix-ui/primitive`, `react-compose-refs`, `react-context`,
`react-primitive`, `react-use-controllable-state`, `react-use-effect-event`,
`react-use-layout-effect`, and `react-use-size`. All are published by the same
project under the MIT License and the same copyright notice reproduced below.

`gifenc` runs only after a user chooses a GIF. It re-encodes the file locally
when that can produce a smaller lossless result; no media is sent away.

## Project assets

The bundled GIFs in `playground/` (`heart-kiss`, `blushing-cat`,
`confused-cat`, `math-cat`, `side-eye-kid`, `ew-dog`, `bleh-cat`,
`yes-sir-cat`, `husky-dance` and `battle-cat`) were supplied by the project
owner for inclusion as the Video Playground's built-in GIFs.

## Local face detection and model

The primary detector uses `@mediapipe/tasks-vision` 0.10.32, copyright Google
LLC and the MediaPipe authors, under the Apache License 2.0. Its JavaScript
worker, WASM loader and WASM binary are packaged locally. The unmodified loader
and binary in the extension's `face-models/wasm/` directory come from that npm
package.

The packaged `face_landmarker.task` is Google's
[Face Landmarker float16 model, version 1](https://storage.googleapis.com/mediapipe-models/face_landmarker/face_landmarker/float16/1/face_landmarker.task),
SHA-256 `64184e229b263107bc2b804c6625db1341ff2bb731874b0bcc2fe6544e0bc9ff`.
The bundle combines face detection, facial landmarks and blendshape models;
YouScroll disables blendshape output. The upstream
[Face Landmarker overview](https://developers.google.com/edge/mediapipe/solutions/vision/face_landmarker)
links the relevant model cards and Apache License 2.0 terms. These links record
provenance; the extension does not download code or models at runtime.

The complete Apache License 2.0 is included as `LICENSE` in the distributed
extension.

### Local JavaScript fallback

The content script includes a TypeScript adaptation of the cascade evaluator
from [pico.js](https://github.com/nenadmarkus/picojs/tree/afffa50ec4134a47005f2cbf8112eaa69f65f37e)
by Nenad Markus and the `facefinder` cascade from
[pico](https://github.com/nenadmarkus/pico/tree/7d550c78b2c31a4e1dfc5bcdfe9da013297b5cc8),
both under the MIT License. The decoded cascade has SHA-256
`d8014993e7298c7b1865d1f8b855d6dbf4ec5c808bf879e2091ab6837abf90cd`.
Both are bundled with the extension and never downloaded while watching. No
upstream webcam code is included.

Reference: N. Markus, M. Frljak, I. S. Pandzic, J. Ahlberg and R. Forchheimer,
"Object Detection with Pixel Intensity Comparisons Organized in Decision
Trees," [arXiv:1305.4537](https://arxiv.org/abs/1305.4537).

## Build-generated runtime and CSS

The following packages contribute generated runtime code or CSS to the
distributed extension and are provided under the MIT License:

| Package             | Version | Distributed contribution            | Source                                                                           |
| ------------------- | ------- | ----------------------------------- | -------------------------------------------------------------------------------- |
| Vite                | 8.1.5   | Module-preload runtime              | https://github.com/vitejs/vite/tree/v8.1.5/packages/vite                         |
| @crxjs/vite-plugin  | 2.7.1   | Content-script loader runtime       | https://github.com/crxjs/chrome-extension-tools/tree/v2.7.1/packages/vite-plugin |
| Tailwind CSS        | 3.4.19  | Preflight and generated utility CSS | https://github.com/tailwindlabs/tailwindcss/tree/v3.4.19                         |
| tailwindcss-animate | 1.0.7   | Generated animation CSS             | https://github.com/jamiebuilds/tailwindcss-animate/tree/v1.0.7                   |

## MIT License

Applies to React, React DOM, the Radix UI primitives, clsx, tailwind-merge,
gifenc, the pico adaptation and cascade, Vite, @crxjs/vite-plugin, Tailwind CSS,
and tailwindcss-animate, each under its own copyright notice:

Copyright (c) Facebook, Inc. and its affiliates.

Copyright (c) 2022 WorkOS

Copyright (c) Luke Edwards <luke.edwards05@gmail.com> (lukeed.com)

Copyright (c) 2021 Dany Castillo

Copyright (c) 2017 Matt DesLauriers

Copyright (c) 2013 Nenad Markus (pico and facefinder)

Copyright (c) Nenad Markus (pico.js)

Copyright (c) 2019-present, VoidZero Inc. and Vite contributors

Copyright (c) 2019 jacksteamdev

Copyright (c) Tailwind Labs, Inc.

Copyright (c) 2020 Jamie Kyle

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

## ISC License

Applies to lucide-react:

Copyright (c) for portions of Lucide are held by Cole Bemis 2013-2022 as part
of Feather (MIT). All other copyright (c) for Lucide are held by Lucide
Contributors 2022.

Permission to use, copy, modify, and/or distribute this software for any
purpose with or without fee is hereby granted, provided that the above
copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.

## YouScroll's own license

YouScroll is licensed under the Apache License 2.0. The complete license is
included as `LICENSE` in the distributed extension.

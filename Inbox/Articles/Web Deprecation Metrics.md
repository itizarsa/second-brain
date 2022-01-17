# Web Deprecation Metrics

Source: Website
Status: Unprocessed
URL: https://deprecate.it/

## [§](https://deprecate.it/) `document.domain`

`document.domain`'s ability to relax the same-origin policy, allowing two same-site pages to synchronously script each other, is a footgun. It complicates the implementation of the single defensible security boundary the web can reasonably uphold, and confounds our ability to cleanly map that boundary onto an underlying process. Ideally, we'll be able to [remove this behavior from the platform](https://github.com/mikewest/deprecating-document-domain), as part of a broader shift towards origin-level isolation by default.

The data below is gathered from [Chrome's usage statistics](https://chromestatus.com/metrics/feature/popularity), and represents the percentage of Chrome page loads that are affected by `document.domain` either allowing or blocking a cross-origin access that would have behaved otherwise in its absence.

## [§](https://deprecate.it/) Unisolated `SharedArrayBuffer`

TODO: explain.

## [§](https://deprecate.it/) MIME Sniffing

TODO: explain.

### Same-Origin MIME Mismatches

### Cross-Origin MIME Mismatches

### Worker Mismatches

## [§](https://deprecate.it/) Private Network Access

TODO: explain.

### Private Network Access from Nonsecure Contexts

### Private Network Access from Secure Contexts

## [§](https://deprecate.it/) `javascript:` URLs

TODO: explain.

## [§](https://deprecate.it/) Bad Markup

TODO: explain.

## [§](https://deprecate.it/) <object> and <embed>

TODO: explain.

## [§](https://deprecate.it/) WASM Module Sharing

TODO: explain.
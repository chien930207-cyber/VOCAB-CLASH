# VOCABCLASH App-ready delivery verification

Release: vc-app-r2. Date: 2026-10-06.

## Baseline and scope

The baseline is VocabClash-Neon-No-Lobby-Logo.zip, not the early Firebase prototype.
The actual ARCO-v2.5.0-Logo-Ready.zip was inspected. Its relative manifest identity,
start_url and scope (all ./), standalone display mode and Apple declarations were
compared against this release. The previous VOCAB release already declared
standalone; this update verifies those fields, versions icon resource paths and
adds safe-area layout and clear installation guidance.

All 14 existing script bodies are byte-identical, including data, game authority,
networking, tutorial, audio, learning and presentation. A 15th script only manages
installation guidance and browser installation events. No service worker, cache
purge, database migration, tracking, cloud sync or server-side deployment was added.
The lobby has a text-only VOCABCLASH wordmark and zero graphic logos in its intro.
Header artwork is preserved. The approved Chinese headline is unchanged.

## Executed checks

| Check group | Passed / executed |
| --- | --- |
| structural | 21 / 21 |
| http | 28 / 28 |
| layouts | 13 / 13 |
| tour | 78 / 78 |
| features | 10 / 10 |

The 13 layout checks are six lobby widths, six settings widths and one synthetic
safe-area inset test. The 78 tutorial cases are 13 steps across six viewports.
All 18 demonstration cases were remeasured against the actual demo card, not the
full-screen dimming backdrop. This corrected a test-selector mistake, not an app
layout defect. There is no overlap between the visible demo/target and explanation.

Additional fresh-page solo smoke: actual basic practice started with 10.0s shown,
accepted an answer, advanced to round 2, and returned to the lobby. No browser
pageerror was recorded. No real multiplayer suite was rerun for this delivery.
The prior release's larger game test totals are not claimed as newly executed.

Ten PNG resources have the advertised dimensions and opaque RGB mode. Both ICO
resources include 16/32/48px frames. Versioned images are byte-identical copies of
the existing assets; there is no new vector master or higher-resolution source art.

The 28 resource checks use actual Python HTTP requests to two local servers:
a project subdirectory and a domain root. They validate resource existence,
image dimensions, manifest MIME/JSON, relative start_url/id/scope and maskable entries.
This is not a browser installation test. The included logo-check.html is for the
owner to run on the published site; its normal browser fetch flow was not tested
against a live GitHub Pages URL here.

## Browser method and limits

Normal browser URL navigation is blocked with ERR_BLOCKED_BY_ADMINISTRATOR.
Rendering therefore uses Playwright set_content with the actual self-contained
preview HTML, not an attempt to bypass administrator policy. HTTP resources were
independently requested by Python. UI captures are real browser-rendered pages,
not device-home-screen mockups. The standalone indicator was tested with a
synthetic navigator.standalone flag; it does not prove OS installation.

Not verified: physical iPhone/iPad/Android icons or launch behavior, real desktop
installation, existing shortcut cache refresh, public GitHub Pages, cross-network
PeerJS, real speaker/vibration hardware, persistent IndexedDB after browser restart.
The preview file intentionally has no external manifest and is not the deployable
installation entry. Use the index.html and resources in the ZIP on HTTPS.

## Integrity

Baseline HTML SHA-256: `f6b7721176a298a911b97994d1c0362e25bba0931abf1184cc2541c611acdce4`

Release index.html SHA-256: `3a6a91fce79438e544ac14779d7ecbd89c0f5e8b8f53b17063a4bac244eb5634`

Machine-readable summary: APP-CHECKS.json.

---
version: 1
slug: "index-html"
primary_target: "index.html"
related_targets: []
---

## Scope

`index.html` — the entire product. One screen, opened by an NFC tap from a commemorative keychain.

## Visitor mode

**Operate.** Success is the student reaching a resource, not admiring the page. Scanability and thumb reach outrank expression; the celebration lives in precise details rather than in narrative or persuasion. The page must never make a student hunt for a link in order to appreciate a composition.

## Audience and job

Graduating students of Campus Estado de México, ADSC '26, standing up, one-handed, on cellular, for well under a minute, holding the keychain that just opened the page. They arrive with no prior intent and no navigation history.

## Action

Tap one of five external destinations. All five are equal in weight — no primary CTA, no ranking. Nothing else on the page is a target.

## Content and constraints

- Five links, fixed order, URLs verbatim including their tracking parameters (`ref=KARFAB-KARFAB`, `srsltid=…`).
- Required marks: the anniversary seal (primary, visible), a graduation cap for Journey, the EXATEC wordmark, the Emprendimiento bolt, the Tec torch for both Centro de Vinculación and Posgrados.
- User declined a countdown, a contact line, and social handles. Adding content sections is out of scope, not an oversight.
- Spanish (es-MX). No graduation date, contact, handles, or photography exist — future work must not invent them.

## Chosen direction

**Orden de ceremonia** — the printed graduation programme. Assigned by roll (seed `1bfbf792`, candidate 4 of the grounded list) over challengers Star Atlas, Cutting Bench Select Rail, and Datamatics, none of which won on both audience identification and product clarity; the two strongest each failed on a binding brand commitment (displacing Tec blue) or on identification.

The page is a programme for a ceremony that has not happened yet: a drenched Tec-blue cover, the seal tipped on as a white paper plate inside a double engraved rule, and the five destinations set as ruled entries — roman numeral, name, dotted leader rule — rather than as a stack of pills.

## Memorable moment

The programme is pressed, then ruled in: the seal plate settles from a blur as a foil stamp would, and each dotted leader rule draws left-to-right beneath its entry in sequence. One orchestrated moment, gated entirely on `prefers-reduced-motion: no-preference`, so the static page is the default rather than the fallback.

## Notes for future work

- The dotted rules are separators, not inline leaders. This was a deliberate engineering choice: the long "Centro de Vinculación y Desarrollo Profesional" label wraps to two lines on a phone, and an inline leader between name and mark collapses to nothing there. Do not "restore" inline leaders without re-solving that wrap.
- Row marks are reversed to white and sized **optically, not uniformly** — the EXATEC wordmark is set far shorter than the symbol marks. Equalizing their heights is a regression, not a cleanup.
- Two rows legitimately share the torch mark. That is the user's instruction, not a duplication bug.

## Unresolved

- "ADSC" was deliberately left unexpanded; the user kept the acronym students already use.
- The deploy host is not yet chosen. The build assumes relative paths and works from any static root or subpath.
- **Deploy blocker:** `og:image` is still a relative path. WhatsApp and Slack do not resolve relative `og:image`, and re-sharing over WhatsApp is the likeliest way this link spreads, so it must become an absolute `https://…/assets/og.png` once the host is known. Flagged with a `DEPLOY:` comment in `index.html`.
- Two sibling project directories exist: `Tec50años2` (this one) and `tec50Años`. Confirm which one deploys before publishing.

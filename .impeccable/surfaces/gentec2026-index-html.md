---
version: 1
slug: "gentec2026-index-html"
primary_target: "gentec2026/index.html"
related_targets: []
---

---
version: 1
slug: "index-html"
primary_target: "index.html"
related_targets: []
---

## Scope

`gentec2026/index.html` — the entire product. One screen, opened by an NFC tap from a commemorative keychain.

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
- Row marks are reversed to white and sized **optically, not uniformly**. Equalizing their heights is a regression, not a cleanup.
- Row II carries the EXATEC wordmark **as its name**, not as its mark, and the Tec torch in the mark slot. The client reported label-plus-wordmark as the same word twice. Accepted cost, chosen by the client over three alternatives: three of five rows now show the torch.
- The seal is carried in the **silhouette of the physical keychain** (disc, tab, punched hole), replacing an earlier tipped-on paper rectangle. It shows the object the visitor is holding. The hole is genuinely punched via an SVG mask, and the shadow is `drop-shadow` on a wrapper because a mask clips `box-shadow`. The disc is flat white: the rectangle's double engraved rule and its −0.45° tilt were both removed after the client read them as leftover frames and as misalignment.
- The keychain silhouette is taller than the rectangle it replaced, so the vertical rhythm above the list was tightened to keep **all five links inside the 390x844 first viewport** (last row bottom measures 839px). That invariant outranks seal size: if they conflict again, shrink the disc.
- Two rows legitimately share the torch mark. That is the user's instruction, not a duplication bug.

## Unresolved

- "ADSC" was deliberately left unexpanded; the user kept the acronym students already use.
- **Resolved:** the site deploys to Cloudflare Pages at `https://mevtek.dev/gentec2026/`. It lives in `gentec2026/` at the repo root so the domain root stays free for a separate site later; Pages serves the repo root, so the folder name *is* the subpath. `og:image` and `og:url` are now absolute against that URL.
- Every internal path is relative, so the site is subpath-agnostic: renaming the folder changes the URL and nothing else — except the two absolute `og:` tags, which must be updated by hand.
- Two sibling project directories exist: `Tec50años2` (this one, → `MevDevs/Tec50Linktree`) and `tec50Años` (→ `A01799782/tec50a-os`). Confirm which one deploys before programming the NFC keychains.

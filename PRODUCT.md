# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Stack

Single static `index.html` with inline CSS and local asset files — no build step, no npm. Chosen by the user from an offered set. Deploy target is any static host (GitHub Pages / Netlify / Vercel); the repository is already named `Tec50Linktree`. The one-request constraint is a product requirement, not a preference: the page is opened by an NFC tap, often on cellular data, and must paint immediately.

## Users

Graduating students ("Candidatos a Graduar") of Campus Estado de México, ADSC generation 2026. They arrive one way: they receive a physical graduation gift box, pick up a commemorative "50 Años Tec Campus Estado de México" keychain, and tap it against their phone. The NFC chip opens this page.

The situation is specific and shapes everything: the user is holding a keychain in one hand and a phone in the other, standing up, probably among other people, probably for less than thirty seconds. They are not browsing. They did not search for this. Their job is to find out what this thing points to and to bookmark or follow one link that matters to their life after graduation.

## Product Purpose

Be the digital half of a physical gift. The keychain is the memento; this page is what the memento *does*. It routes a student who is weeks away from graduating to the five institutional resources that stay useful after they stop being a student: their graduation journey, the alumni network, career services, the entrepreneurship community, and graduate studies.

Success is a student tapping through to at least one resource, and the page feeling like part of the gift rather than a link dump attached to it.

## Positioning

This is not a Linktree account and must not read as one. It is a commemorative object's screen — the 50th-anniversary campus seal is the reason the keychain exists, so the seal is the page's subject, not its watermark. A generic link-in-bio page could carry the same five URLs; it could not carry the anniversary.

## Operating Context

- **Entry:** NFC tap from a physical keychain. There is no referrer, no navigation, no back button to anywhere. This page is the whole session.
- **Device:** mobile phones, overwhelmingly. Portrait. One-handed. Assume thumb reach matters and that the top of the screen is the hardest place to touch.
- **Network:** cellular, possibly on a crowded campus. First paint must not wait on a font CDN or a framework.
- **Moment:** the gift box is handed out close to graduation. The emotional register is celebratory and slightly valedictory — "esto se acaba" and "esto empieza" at once.
- **Language:** Spanish (es-MX) throughout. All copy, all labels.

## Capabilities and Constraints

Confirmed scope — strictly a Linktree structure: a profile/header block followed by one vertical list of five link buttons, plus a minimal footer. The user explicitly declined a countdown, a contact line, and social handles. No extra sections, no landing-page narrative.

The five destinations, in this exact confirmed display order (extracted from `Ligas para el linktree.docx`; note the document's own numbering differs from the required display order):

1. **Journey de Graduación** — `https://view.genially.com/65bd175a922a3a001460ac42`
2. **EXATEC** — `https://tec.mx/es/exatec?srsltid=AfmBOorhCR7Jp0UaISbtzIIOJq-1Tk8Tja-yZ-WXmamy7YEkKEPUP5kF`
3. **Centro de Vinculación y Desarrollo Profesional** — `https://cvdp.tec.mx/es`
4. **Emprendimiento** — `https://linktr.ee/emprendimientoTECcem`
5. **Posgrados** — `https://posgrados-admisiones.tec.mx/organizaciones-oferta?ref=KARFAB-KARFAB`

All five are external and open in a new tab. The Posgrados URL carries a `ref=KARFAB-KARFAB` attribution parameter and the EXATEC URL a `srsltid` token; both are preserved verbatim — they are tracking-bearing and must not be "cleaned up".

Header wording leads with the celebration ("¡Felicidades, Generación 2026!") and carries "Campus Estado de México" and "ADSC '26" as supporting identification. "ADSC" is kept as the acronym students already use; it was not expanded.

## Brand Commitments

- **Tecnológico de Monterrey** institutional identity. Tec blue is the anchor color; the 50th-anniversary seal introduces a second, lighter indigo that the page may treat as a legitimate secondary.
- **Required, binding asset placement:**
  - The 50th-anniversary seal must be visibly present as a primary element, not a footnote.
  - Journey de Graduación → a graduation-cap icon (no supplied asset; must be drawn).
  - EXATEC → the supplied EXATEC wordmark.
  - Emprendimiento → the supplied Emprendimiento bolt logo.
  - Centro de Vinculación **and** Posgrados → the supplied Tec torch mark, correctly cropped so it sits as a proper icon rather than as a rectangular blue tile.
- Voice: Spanish, warm, institutional but not stiff. This is the campus congratulating its own students.

## Evidence on Hand

Real assets in the repository root, all verified to render:

| File | What it is | Notes for use |
|---|---|---|
| `Sello-50-aniversario.ai` | 50th-anniversary seal | PDF-1.6 internally; converts losslessly to SVG via `pdftocairo -svg`. Two blues: indigo "50" + Tec navy "TEC". Contains hidden optional-content layers. |
| `Exatec-logo.jpg` | EXATEC wordmark | 474×99, blue on white, no alpha. Wide aspect — needs a lockup slot, not a square one. |
| `Emprendimiento-logo.jpeg` | Bolt mark | 446×448, square, white/lavender bolt on dark navy. No alpha; the navy field is part of the mark. |
| `other-logo.png` | Tec torch mark | 486×322 with alpha, but the torch circle sits inside a solid blue rectangle. Must be cropped to the circle before use. |

`Ligas para el linktree.docx` is the source of record for the URLs and has been fully extracted; nothing else in it is needed.

No graduation date, no contact address, no social handles, and no photography were provided. Future work must not invent any of them.

## Product Principles

1. **The tap is the whole session.** One screen, one purpose, no navigation. Anything that does not help a student reach a link is weight.
2. **Five links, one order, verbatim URLs.** The order is fixed and the tracking parameters are load-bearing.
3. **The seal is the subject.** The anniversary is why the physical object exists; the page inherits that, and the seal earns real size.
4. **Thumb-first, not desktop-shrunk.** Targets, spacing, and reading order are designed for a phone held in one hand and validated there first.
5. **First paint beats everything.** No framework, no blocking font fetch, no layout shift. The page is ready before the student's thumb is.

## Accessibility & Inclusion

Mobile-first with real touch targets (≥44px, comfortably larger in practice). Text must survive OS-level font scaling. Link purpose must be clear from the link text alone — icons are reinforcement, never the only label. Contrast must hold at AA against the Tec blue field, and motion must respect `prefers-reduced-motion`, since the page's celebratory feel should never cost a student who has that preference set.

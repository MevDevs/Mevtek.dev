---
name: Candidatos a Graduar · Campus Estado de México
description: The digital half of a commemorative keychain — a graduation programme for a ceremony that has not happened yet.
colors:
  cover: "#00265F"
  cover-deep: "#001A42"
  cover-lift: "#0B3A7F"
  paper: "#FFFFFF"
  seal-ink: "#000F35"
  tec-blue: "#0039A6"
  seal-indigo: "#445AA2"
  muted: "#A8BEE6"
typography:
  display:
    fontFamily: "Archivo, ui-sans-serif, system-ui, sans-serif"
    fontSize: "clamp(2rem, 8.6vw, 2.9rem)"
    fontWeight: 800
    lineHeight: 0.99
    letterSpacing: "-0.028em"
  entry:
    fontFamily: "Archivo, ui-sans-serif, system-ui, sans-serif"
    fontSize: "clamp(1.0625rem, 4.3vw, 1.1875rem)"
    fontWeight: 600
    lineHeight: 1.24
    letterSpacing: "-0.012em"
  signature:
    fontFamily: "Archivo, ui-sans-serif, system-ui, sans-serif"
    fontSize: "0.75rem"
    fontWeight: 600
    lineHeight: 1.65
    letterSpacing: "0.14em"
  label:
    fontFamily: "Archivo, ui-sans-serif, system-ui, sans-serif"
    fontSize: "0.6875rem"
    fontWeight: 700
    lineHeight: 1.4
    letterSpacing: "0.24em"
  display-narrow:
    fontFamily: "Archivo, ui-sans-serif, system-ui, sans-serif"
    fontSize: "1.8rem"
    fontWeight: 800
    lineHeight: 0.99
    letterSpacing: "-0.032em"
  display-wide:
    fontFamily: "Archivo, ui-sans-serif, system-ui, sans-serif"
    fontSize: "2.5rem"
    fontWeight: 800
    lineHeight: 0.99
    letterSpacing: "-0.028em"
  caption:
    fontFamily: "Archivo, ui-sans-serif, system-ui, sans-serif"
    fontSize: "0.75rem"
    fontWeight: 400
    lineHeight: 1.7
    letterSpacing: "0.005em"
rounded:
  plate: "3px"
  plate-inner: "1px"
  entry: "6px"
spacing:
  gutter: "clamp(1.25rem, 5.5vw, 2rem)"
  entry-y: "1.05rem"
  section: "clamp(2.25rem, 8vw, 3rem)"
  column: "31rem"
components:
  entry:
    backgroundColor: "transparent"
    textColor: "{colors.paper}"
    typography: "{typography.entry}"
    rounded: "{rounded.entry}"
    padding: "1.05rem 0.25rem"
    height: "68px"
  entry-hover:
    backgroundColor: "rgba(255,255,255,0.075)"
    textColor: "{colors.paper}"
    rounded: "{rounded.entry}"
  seal-plate:
    backgroundColor: "{colors.paper}"
    rounded: "{rounded.plate}"
    padding: "0.5rem"
    width: "min(72%, 17.5rem)"
---

# Design System

## Overview

This surface is a **printed graduation programme**, not a link-in-bio page. The distinction governs every decision below: a programme has a cover, a seal, a section rule, and an ordered list of proceedings set in ruled entries. It does not have avatars, pills, or cards.

The page exists as the digital half of a physical object. A graduating student taps a commemorative 50th-anniversary keychain and this opens. That scene — standing up, one hand, cellular data, under a minute — makes the visitor mode **Operate**: success is reaching a resource, not admiring the composition. The celebration is carried in precise details (the seal at real scale, engraved rules, the ceremonial numerals), never in narrative or persuasion.

Colour strategy is **Drenched**: the surface *is* Tec blue. The one white element on the page is the seal plate, which is why the seal reads as the subject rather than as a logo parked in a corner.

## Colors

`cover` #00265F is the ground and owns effectively the whole surface. It is not a background behind content; it is cover stock. `cover-lift` and `cover-deep` exist only as the two ends of a single raking-light gradient down the page — they are never used as fills, borders, or accents.

`paper` is reserved for the seal plate. Introducing a second white panel would destroy the plate's status as the tipped-in element.

`seal-ink`, `tec-blue`, and `seal-indigo` are sampled from the anniversary artwork itself (the "50" is indigo, "TEC" is Tec blue, the lettering is near-black navy).

`seal-indigo` is the **second ink**, and it earns that name by being used: the plate's double engraved rule is drawn in it, on white, at 18–34% — a programme rule printed in the seal's own colour. It is never used on the blue ground, where it measures only 2.24:1 and cannot legally carry text.

`muted` #A8BEE6 is the only secondary text colour and is tinted from the ground's own hue. It measures 7.75:1 on `cover`; white body text measures 14.5:1. **Never use a neutral grey for secondary text on this ground** — it goes muddy against saturated blue.

## Typography

One family, Archivo variable, carrying both `wght` (400–800) and `wdth` (62–125) axes, self-hosted at `assets/fonts/archivo-latin.woff2`, preloaded, `font-display: swap`.

**Keep it external.** Inlining the subset as a base64 data URI was tried and reverted: it puts ~120KB inside a render-blocking `<style>`, so nothing paints until the whole block arrives — on the crowded-campus cellular scene this product is built for, that inverts Product Principle 5. An external woff2 paints the field and all text in one round trip and swaps the face in. The cost is that opening the file directly from disk (`file://`) shows fallback type, because browsers block cross-origin font loads there; preview over a local HTTP server instead.

The ramp is short and the steps are unambiguous:

| Role | Size | Weight | Character |
|---|---|---|---|
| `display` | clamp(2rem, 8.6vw, 2.9rem) | 800, `wdth` 113 | The congratulation. Slightly expanded, tight tracking. Used once. |
| `entry` | clamp(1.0625rem, 4.3vw, 1.1875rem) | 600 | The five destination names. |
| `signature` | 0.75rem | 600, +0.14em, caps | The identifying line under the headline. |
| `label` | 0.6875rem | 700, +0.24em, caps | Section label and the roman numerals. |
| `caption` | 0.75rem | 400 | Colophon. |
| `display-narrow` | 1.8rem | 800, `wdth` 113 | The cover line at ≤359px, tracked tighter, so "Generación 2026!" holds one line instead of orphaning "2026!". |
| `display-wide` | 2.5rem | 800, `wdth` 113 | The same cover line from 640px up. A deliberate step **down** from the phone clamp's 2.9rem ceiling, so the whole programme fits one laptop screen. |

On OS-level font scaling: only `entry` actually tracks it at phone width — its `4.3vw` term (16.8px at 390) falls below its `1.0625rem` floor, so the clamp resolves to rem and scales. `display` and the gutter resolve to their `vw` terms at 390 and do **not** respond to root font size. That is an accepted trade for a fixed-purpose single screen, not a general rule to copy: if this ramp is reused on a text-heavy surface, re-bound the display step in `rem`.

The cover line is the only role with responsive steps, and it has three: `display-narrow` at ≤359px, the `display` clamp between, `display-wide` from 640px. Every other role is a single value at every width.

Expanded width (`wdth` 113) belongs to the display line only. Widening the entry names flattens the hierarchy the ramp exists to create.

## Layout

Single centred column, `31rem` max, gutters `clamp(1.25rem, 5.5vw, 2rem)`, with `env(safe-area-inset-*)` added on all four sides for notched phones (`viewport-fit=cover`).

Two breakpoints, both earning their place:

- **≤359px** — the narrowest phones buy width back from the numeral column and gutters, never from the touch target.
- **≥640px** — the seal and vertical rhythm tighten so the entire programme sits in one laptop screen. Desktop is a courtesy view; the phone is the truth.

Rhythm: more space above a heading than below it. The section label sits tight to its rule, and the rule sits tight to the first entry.

## Elevation & Depth

Exactly one elevated object: the seal plate. `0 22px 44px -14px rgba(0,0,0,.55)` plus a tighter `0 6px 14px -6px rgba(0,0,0,.38)` — real vertical offset, real blur, neutral colour. Depth on this page means *a piece of paper is lying on the cover*, so it must read as a cast shadow, never as a glow.

The plate also carries `rotate(-.45deg)` — tipped on by hand rather than machine-centred. This is real geometry, not a simulated material effect; the cast shadow rotates with it. The rotation is baked into the `sello` keyframes so the press-in does not unwind it.

No other element is raised. There is no glass, no blur decoration, and no coloured halo anywhere.

## Shapes

Corners are nearly square and deliberately so: `3px` on the plate, `1px` on its inner engraved rule, `6px` on the entry press area. The form language is print, and print does not have 16px radii.

The plate's **double rule** — outer paper edge plus a 1px inner border at 16% ink — is the certificate device that makes the plate read as ceremonial stationery rather than as a card.

Separators are **dotted leader rules**: `repeating-linear-gradient(to right, var(--rule) 0 2px, transparent 2px 6px)`, 2px tall. They are the programme's contents-page grammar and are the only decorative line on the page.

## Components

**Entry** — the only interactive component. A three-column grid: roman numeral / name / mark, with a dotted leader rule between rows. 68px tall minimum (75.8px when the name wraps to two lines), full column width, so the whole row is the target. Press and hover both resolve to a 7.5% white wash; focus-visible adds a 2px white outline at 2px offset.

**Seal plate** — the header's white paper plate. One per page, always.

**Marks** — logos reversed to white on transparent, sized **optically rather than uniformly**: symbol marks (torch, bolt, cap) sit at ~1.75–1.9rem, the EXATEC wordmark at 0.95rem. Equalising these heights is a regression. Every mark is `aria-hidden`; the link text alone carries the link's purpose.

**Motion** — one authored moment, gated entirely inside `@media (prefers-reduced-motion: no-preference)` so the static page is the default rather than the fallback. The seal presses in from a blur, then each dotted rule draws left-to-right beneath its entry on a 40ms stagger, complete by ~0.87s. Easing is `cubic-bezier(.16,1,.3,1)` throughout.

**No text is ever hidden to stage this.** An earlier build faded every element up from `opacity:0`, which left the fifth link invisible until 0.74s on a page whose only success metric is a tap. Motion may move what is already painted; it may not fade in text.

## Do's and Don'ts

**Do**
- Keep the ground drenched. Blue owns the surface; white is a guest.
- Tint every secondary text colour from the ground's hue.
- Size marks optically, by how big they *look*, not by a shared box.
- Bound type in `rem` so OS font scaling still works.
- Keep the whole row tappable and above 44px.

**Don't**
- Don't introduce cards, pills, or a second white panel. The plate is the only paper.
- Don't add a coloured glow, a radial halo, or a zero-offset shadow.
- Don't equalise the mark heights or re-colour the logos.
- Don't use grey for secondary text.
- Don't reintroduce inline leader dots between name and mark — the long "Centro de Vinculación y Desarrollo Profesional" label wraps on a phone and collapses them to nothing. The rules are separators for that reason.
- Don't add content sections. The five links are the settled scope.
- Don't stage content by hiding it. Motion may move what is already painted; it may not fade in text.
- Don't inline the font to save a request — see Typography.

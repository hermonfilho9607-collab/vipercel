# Design System Master File

> **LOGIC:** When building a specific page, first check `design-system/vipercel/pages/[page-name].md`.
> If that file exists, its rules **override** this Master file.
> If not, strictly follow the rules below.

---

**Project:** Vipercel
**Generated:** 2026-09-16 13:17:49
**Revised:** manually overridden after grounding in the client's own assets (`logo.jpg`, `Referencia.html` → Pinterest board "Velocia Motors" + "Auto Reborn" dark automotive landing pages) and the client's explicit style pick — see rationale below
**Category:** Loja de celulares/eletrônicos com foco em assistência técnica especializada, posicionamento institucional (sem carrinho — conversão via WhatsApp), one-page
**Design Dials:** Variance 6/10 (Balanced / Modern) | Motion 7/10 (Standard–Complex) | Density 3/10 (Spacious)

---

## Why this overrides the auto-generated defaults

The `--design-system` search for "electronics repair store tech premium dark" returned a generic **"E-commerce Luxury"** preset (light `#FAFAF9` background, Liquid Glass / Apple system-chrome style, Cormorant+Montserrat fashion-luxury serif pairing, gold accent). The word "premium" pulled it toward fashion/jewelry e-commerce — that preset does not match the brief at all.

Two follow-up domain searches gave a correct, verified base instead:
- `product` search "automotive premium landing bold" → **Automotive/Car Dealership** (Motion-Driven + 3D/Hyperrealism, secondary Dark Mode OLED + Glassmorphism, Hero-Centric + Feature-Rich pattern, "Brand colors + Metallic accents + Dark")
- `style` search "bold editorial dark typography" → **Exaggerated Minimalism** (oversized clamp typography, font-weight 900, black/white + single accent, massive whitespace) — matches the huge "velocia" wordmark treatment seen directly in the client's reference screenshots

This tracks exactly with the client's own reference: two Pinterest pins of dark, cinematic automotive landing pages (near-black background, dramatic rim-lit product photography, oversized bold wordmark, small high-contrast accent CTA, stat callouts, icon+label feature grid). The client confirmed **"Escuro e cinematográfico"** (dark and cinematic) when asked directly how much of that intensity to carry over.

Palette, type and style below are rebuilt from the client's actual logo (`logo.jpg`, pixel-sampled) and the reference mood. Spacing/shadow/motion mechanics follow the same dial logic the generator uses.

### Color Palette

| Role | Hex | CSS Variable | Usage |
|------|-----|--------------|-------|
| Background | `#0A0C16` | `--color-bg` | Base page color — near-black with a cold blue undertone (not pure `#000`), ties the whole shell back to the brand hue |
| Surface | `#12141F` | `--color-surface` | Cards, raised panels, nav-on-scroll |
| Surface Deep | `#06070D` | `--color-surface-deep` | Footer, solid nav bar, any full-bleed dark rail |
| Foreground | `#F5F6FA` | `--color-fg` | Primary text on dark — cool off-white, never flat `#FFF` |
| Muted Foreground | `#8D93AC` | `--color-fg-muted` | Secondary text, captions, labels |
| Border | `rgba(245,246,250,0.08)` | `--color-border` | Hairlines on dark surfaces |
| Brand Blue | `#072E95` | `--color-brand` | Sampled directly from `logo.jpg` (RGB 7,46,149). Large fills, nav-solid, footer, section dividers, secondary surfaces — the "identity" color |
| Accent/CTA | `#3358E8` | `--color-accent` | Brighter interactive tint of the brand blue — buttons, links, focus rings, active states. Brand Blue alone is too dark to read as "clickable" on a near-black page |
| On Accent | `#FFFFFF` | `--color-on-accent` | |
| Glow | `#6C8CFF` | `--color-glow` | Sparingly: icon glows, gradient highlights, the "rim light" edge on product photography treatments |
| WhatsApp | `#25D366` | `--color-whatsapp` | Tactical exception, WhatsApp CTA button only (floating button + hero secondary CTA) — instantly recognizable affordance, kept separate from the brand-blue system |
| On WhatsApp | `#FFFFFF` | `--color-on-whatsapp` | |
| Destructive | `#EF4444` | `--color-destructive` | Form errors only |
| On Destructive | `#FFFFFF` | `--color-on-destructive` | |

**Color Notes:** No gold, no neon, no cyberpunk accents — the dataset's "Dark Mode (OLED)" entry suggests neon green/magenta accents; deliberately not used here. The only two accent hues on the whole site are Vipercel blue (brand) and WhatsApp green (one CTA, functional). Confirm `#072E95` against the client's brand guideline if one exists — it was pixel-sampled from the corner background of `logo.jpg`, not supplied as a spec value.

**Dark-surface shadows:** `box-shadow` is close to invisible on `#0A0C16`. Elevation is expressed with a 1px lighter border (`--color-border`) plus, where the reference's rim-lighting mood needs it, a soft blue glow: `box-shadow: 0 0 60px rgba(51, 88, 232, 0.25)` behind hero product photography — never a generic black drop-shadow.

### Typography

- **Heading / display / hero wordmark:** Barlow Condensed (600–800) — tall, condensed, impactful; echoes the logo's own angular condensed wordmark and the oversized "velocia"-style hero treatment from the reference
- **Body / UI / labels:** Inter (400–500–600) — neutral, highly legible at small sizes, solid diacritics support for Portuguese (ç, ã, é, ê)
- **Mood:** bold, technical, cinematic — deliberately sans-only, no serif anywhere (a serif pairing is what made the auto-generated preset read as "luxury fashion" instead of "premium tech")
- **Google Fonts:** [Barlow Condensed + Inter](https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@500;600;700;800&family=Inter:wght@400;500;600;700&display=swap)

**CSS Import:**
```css
@import url('https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@500;600;700;800&family=Inter:wght@400;500;600;700&display=swap');
```

**Scale (fluid, clamp-based):**

| Role | Mobile → Desktop | Weight | Line-height | Tracking |
|------|---|---|---|---|
| Hero wordmark | `clamp(3rem, 12vw, 9rem)` | 800 (Barlow Condensed) | 0.95 | -0.01em |
| H2 section | `clamp(2rem, 4.5vw, 3.5rem)` | 700 (Barlow Condensed) | 1.05 | 0 |
| H3 / card title | `clamp(1.25rem, 2vw, 1.5rem)` | 600 (Barlow Condensed) | 1.2 | 0.01em |
| Eyebrow / label | `0.8125rem` fixed | 600 (Inter), uppercase | 1.3 | 0.12em |
| Body | `1rem–1.0625rem` | 400 (Inter) | 1.6 | 0 |
| Stat number | `clamp(2rem, 4vw, 3rem)` | 700 (Barlow Condensed) | 1 | 0 |

### Spacing Variables

*Density: 3/10 — Spacious*

| Token | Value | Usage |
|-------|-------|-------|
| `--space-xs` | `4px` / `0.25rem` | Tight gaps |
| `--space-sm` | `8px` / `0.5rem` | Icon gaps, inline spacing |
| `--space-md` | `24px` / `1.5rem` | Standard padding |
| `--space-lg` | `32px` / `2rem` | Section padding |
| `--space-xl` | `48px` / `3rem` | Large gaps |
| `--space-2xl` | `64px` / `4rem` | Section margins |
| `--space-3xl` | `96px` / `6rem` | Hero padding |

### Shadow Depths

| Level | Value | Usage |
|-------|-------|-------|
| `--shadow-sm` | `0 1px 2px rgba(0,0,0,0.3)` | Subtle lift on dark surfaces |
| `--shadow-md` | `0 4px 12px rgba(0,0,0,0.4)` | Cards, buttons |
| `--shadow-lg` | `0 10px 30px rgba(0,0,0,0.45)` | Modals, dropdowns, sticky nav-on-scroll |
| `--shadow-glow` | `0 0 60px rgba(51,88,232,0.25)` | Hero product photography, featured cards — the rim-light cue |

---

## Component Specs

### Buttons

```css
/* Primary Button — brand accent blue */
.btn-primary {
  background: #3358E8;
  color: #FFFFFF;
  padding: 14px 28px;
  border-radius: 8px;
  font-family: 'Inter', sans-serif;
  font-weight: 600;
  letter-spacing: 0.01em;
  transition: background 200ms ease, transform 200ms ease;
  cursor: pointer;
}

.btn-primary:hover {
  background: #4A6CF5;
  transform: translateY(-1px);
}

/* Secondary Button — outline, sits on dark */
.btn-secondary {
  background: transparent;
  color: #F5F6FA;
  border: 1px solid rgba(245,246,250,0.24);
  padding: 14px 28px;
  border-radius: 8px;
  font-weight: 600;
  transition: border-color 200ms ease, background 200ms ease;
  cursor: pointer;
}

.btn-secondary:hover {
  border-color: #3358E8;
  background: rgba(51, 88, 232, 0.08);
}

/* WhatsApp Button — tactical exception, functional recognition over brand purity */
.btn-whatsapp {
  background: #25D366;
  color: #FFFFFF;
  padding: 14px 28px;
  border-radius: 999px; /* pill — visually distinct from the squared brand buttons, reads as "chat/contact" */
  font-weight: 600;
  display: inline-flex;
  align-items: center;
  gap: 8px;
  transition: background 200ms ease, transform 200ms ease;
  cursor: pointer;
}

.btn-whatsapp:hover {
  background: #2EE577;
  transform: translateY(-1px);
}
```

### Stat Counter (hero / trust-bar device)

```css
.stat {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.stat-number {
  font-family: 'Barlow Condensed', sans-serif;
  font-weight: 700;
  font-size: clamp(2rem, 4vw, 3rem);
  color: #F5F6FA;
  line-height: 1;
}

.stat-label {
  font-family: 'Inter', sans-serif;
  font-size: 0.8125rem;
  color: #8D93AC;
  text-transform: uppercase;
  letter-spacing: 0.1em;
}
```
Count up from 0 on scroll-into-view (see Motion). Mirrors the reference's "500+ / 30+ / 100%" stat row — Vipercel's equivalents are real numbers the client needs to confirm (years in business, repairs completed, avg. rating, warranty days).

### Cards (service / feature grid)

```css
.card {
  background: #12141F;
  border: 1px solid rgba(245,246,250,0.08);
  border-radius: 12px;
  padding: 32px;
  transition: border-color 200ms ease, transform 200ms ease;
}

.card:hover {
  border-color: #3358E8;
  transform: translateY(-2px);
}
```

### Inputs

```css
.input {
  background: rgba(245,246,250,0.03);
  padding: 14px 16px;
  border: 1px solid rgba(245,246,250,0.12);
  border-radius: 8px;
  color: #F5F6FA;
  font-size: 16px; /* keeps iOS from auto-zooming */
  transition: border-color 200ms ease;
}

.input::placeholder { color: #8D93AC; }

.input:focus {
  border-color: #3358E8;
  outline: none;
  box-shadow: 0 0 0 3px rgba(51, 88, 232, 0.2);
}
```

### Floating WhatsApp Button (persistent, all breakpoints)

```css
.whatsapp-float {
  position: fixed;
  bottom: 24px;
  right: 24px;
  width: 56px;
  height: 56px;
  border-radius: 50%;
  background: #25D366;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 20px rgba(37, 211, 102, 0.4);
  z-index: 1000;
  cursor: pointer;
}
```
Gentle pulse (`box-shadow` ring expand, 2s loop) to draw the eye without being obnoxious; disable entirely under `prefers-reduced-motion`. Keep clear of any bottom sheet / sticky CTA bar on mobile — see `fixed-element-offset` in the UX ruleset.

---

## Style Guidelines

**Style:** Dark Cinematic (Dark Mode OLED base) + Exaggerated Minimalism typography, automotive-landing-page photography treatment adapted to smartphones

**Keywords:** near-black background, oversized bold condensed wordmark, dramatic rim-lit product photography, stat callouts, compact high-contrast CTA, icon+label feature grid, generous negative space

**Best For:** A physical repair/retail business that needs to read as technically credible and premium, not playful or discount-bin — matches the client's own reference choice (automotive dealership landing pages) and the logo's existing dark royal-blue identity

**Signature devices, carried from the reference and re-applied to phones:**
1. **Oversized brand wordmark in the hero** — set in Barlow Condensed at `clamp(3rem, 12vw, 9rem)`, mirroring the reference's huge "velocia" treatment. Open question for the client: the logo mark itself reads "VIPER" (stylized) — confirm whether the hero wordmark should spell out "VIPERCEL" in full or echo the logo's "VIPER" styling with "CEL" treated as a suffix.
2. **Stat row near the hero** — 3 numbers, real client data required (years active, repairs completed, avg. rating/warranty). Animates count-up on first view.
3. **Small, high-contrast accent CTA** — not a giant rounded button; a compact pill/rect that pops against a large dark photo, exactly like the reference's small red CTA against the car shot.
4. **Feature/service grid, 4–6 cards** — icon + short label + one-line description (troca de tela, bateria, placa, diagnóstico, etc. — final list pending client's service catalog).
5. **Floating WhatsApp button** — the one deliberate deviation from the automotive reference, since this brief is "Institucional + WhatsApp" conversion, not e-commerce checkout.

**Photography direction (client is generating images with AI, not supplying real photos):** low-key studio lighting on near-black background, single dramatic rim/edge light in Vipercel blue (`#3358E8`–`#6C8CFF` range) tracing the product silhouette, shallow depth of field, subject (phone, repair tool, technician's hands) sharply lit while the background falls to near-black — same lighting logic as the reference's car photography, translated to product/repair shots. Exact prompts to be handed to the client per-image once page content/sections are finalized.

### Page Pattern

**Pattern Name:** Hero-Centric Design + Feature-Rich Showcase (one-page)

- **Conversion Strategy:** One dominant WhatsApp CTA repeated at hero, mid-page and floating; every section reinforces trust (stats, warranty, reviews) before asking for contact again.
- **CTA Placement:** Hero (primary) + after services grid + floating (persistent) + final CTA band before footer
- **Section Order:** Nav (sticky, transparent → solid on scroll) → Hero (wordmark + tagline + product photo + stat row + WhatsApp CTA) → Trust/stat bar → Serviços (repair grid) → Loja/Produtos em destaque (showcase, no cart) → Diferenciais (garantia, orçamento grátis, peças originais) → Depoimentos → Localização/horário (mapa) → CTA final → Footer (contato, redes sociais, mapa, horário) → Floating WhatsApp button throughout

---

## Motion

Single-page scroll site — motion is scroll-reveal driven, not page-transition driven. Use GSAP + ScrollTrigger:

```js
// Service/feature cards — staggered reveal
gsap.from('.card', {
  opacity: 0, y: 24, duration: 0.5,
  stagger: { each: 0.08, from: 'start' },
  ease: 'power2.out',
  scrollTrigger: { trigger: '.services-grid', start: 'top 80%' }
});

// Stat counters — count up on first view
gsap.from('.stat-number', {
  textContent: 0, duration: 1.2, ease: 'power1.out',
  snap: { textContent: 1 },
  scrollTrigger: { trigger: '.stats-bar', start: 'top 85%', once: true }
});

// Hero product photo — slow ambient drift, text stays fixed
gsap.to('.hero-photo', {
  scale: 1.06, ease: 'none',
  scrollTrigger: { trigger: '.hero', start: 'top top', end: 'bottom top', scrub: true }
});
```

**Framework notes:** `matchMedia('(prefers-reduced-motion: reduce)')` skips all of the above and renders final state immediately — counters show their end value, cards render at full opacity, hero photo stays at `scale(1)`. Keep the WhatsApp float's pulse in this same reduced-motion gate.

---

## Anti-Patterns (Do NOT Use)

- ❌ Liquid Glass / Apple system-chrome styling — that was the wrong auto-generated preset, do not reintroduce it
- ❌ Serif display type (Cormorant, Playfair, etc.) — reads as fashion-luxury, undercuts technical credibility
- ❌ Neon/cyberpunk accent colors (matrix green, magenta, cyan) — stay inside the brand-blue + WhatsApp-green system only
- ❌ Gold/brass accents — that belongs to the wg-vidros project, not this one
- ❌ Playful/rounded "friendly startup" shapes — client confirmed the darker, more serious cinematic direction

### Additional Forbidden Patterns

- ❌ **Emojis as icons** — Use SVG icons (Heroicons, Lucide, Simple Icons — Simple Icons has the official WhatsApp glyph)
- ❌ **Missing cursor:pointer** — All clickable elements must have cursor:pointer
- ❌ **Layout-shifting hovers** — Avoid scale transforms that shift layout
- ❌ **Low contrast text** — Maintain 4.5:1 minimum contrast ratio on the dark background (check `--color-fg-muted` against `--color-bg` specifically — muted text is the easiest place to fall below threshold on dark UI)
- ❌ **Instant state changes** — Always use transitions (150-300ms)
- ❌ **Invisible focus states** — Focus states must be visible for a11y (use `--color-accent` as the focus ring on dark)

---

## Pre-Delivery Checklist

Before delivering any UI code, verify:

- [ ] No emojis used as icons (use SVG instead)
- [ ] All icons from consistent icon set (Heroicons/Lucide/Simple Icons for WhatsApp)
- [ ] `cursor-pointer` on all clickable elements
- [ ] Hover states with smooth transitions (150-300ms)
- [ ] Text contrast 4.5:1 minimum on the dark background, checked separately for muted/secondary text
- [ ] Focus states visible for keyboard navigation
- [ ] `prefers-reduced-motion` respected (counters, stagger, hero drift, WhatsApp pulse)
- [ ] Responsive: 375px, 768px, 1024px, 1440px
- [ ] No content hidden behind fixed navbar or the floating WhatsApp button
- [ ] No horizontal scroll on mobile
- [ ] Logo renders correctly on both `--color-bg` (near-black) and `--color-brand` (solid blue) surfaces — confirm a transparent-background logo file exists for the near-black hero/nav; the current `logo.jpg` has an opaque blue background baked in

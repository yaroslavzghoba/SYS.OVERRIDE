# SYS.OVERRIDE Design System

The design system based on the neo-brutalist geometry, saturated retro hues, terminal-era interfaces, and signs of a world where vegetation has outlived the machines that built it.

The system is intentionally opinionated. It should feel assembled from durable industrial parts, repaired with whatever bright paint and salvaged technology are available. Interfaces are direct, tactile, and slightly raw—but still readable, useful, and accessible.

## 1. Design direction

### The core idea

**Post-apocalyptic retro technology, reclaimed by nature.**

The interface is a surviving system terminal. It reports status, opens archives, broadcasts signals, and exposes project files. The visual shell is mechanical and rigid; the palette is sun-faded but vibrant; organic texture, noise, and video suggest that the outside world is growing back around the machine.

### Four design pillars

1. **Structural honesty** — Borders, spacing, and hierarchy are visible. Avoid decorative containers without a clear purpose.
2. **Tactile impact** — Thick outlines and offset shadows make cards and controls feel physical, like labels bolted onto a console.
3. **Recovered color** — Use warm paper, warning orange, industrial yellow, and oxidized green instead of conventional corporate neutrals.
4. **Readable decay** — Texture, scanlines, dashed rules, and system language may imply age, but they must never interfere with comprehension or interaction.

### Brand vocabulary

Use words that suggest a functioning remnant of an old network:

| UI purpose | Preferred language |
| --- | --- |
| Navigation | `INIT`, `PRJCT`, `ARCHIVE`, `COMMS`, `INDEX` |
| Status | `SYSTEM: STABLE`, `SIGNAL: GOOD`, `NATURE: 78% COVERAGE` |
| Loading | `ARCHIVE_LOAD`, `SYNC_PENDING`, `BOOT_SEQUENCE` |
| Contact | `SIGNAL_BROADCAST`, `TX_READY`, `OPEN_CHANNEL` |
| Actions | `PROJECT_DETAILS_>`, `SEND_E-MAIL`, `OPEN_FILE` |

Use the vocabulary as a layer over plain meaning. Never make a label so cryptic that the user cannot understand its action.

## 2. Color system

### Color palette

| Token | Hex | Role | Recommended use |
| --- | --- | --- | --- |
| `--color-bg-cream` | `#F4E4C1` | Reclaimed paper | Page background, light cards, muted surfaces |
| `--color-orange` | `#E85D04` | Signal orange | Primary feature cards, prominent actions, warnings |
| `--color-yellow` | `#FFBA08` | Hazard yellow | Secondary cards, highlights, attention states |
| `--color-green` | `#556B2F` | Moss / oxidized green | Nature accents, inverse cards, stable status |
| `--color-black` | `#111111` | Carbon black | Text, borders, shadows, high-contrast surfaces |
| `--color-ink-soft` | `#3A3329` | Weathered ink | Secondary text on cream surfaces |
| `--color-cream-dark` | `#D9C397` | Aged paper shadow | Dividers, disabled surfaces, subtle fills |
| `--color-rust` | `#A63D24` | Oxidized metal | Destructive actions, error states, deep accents |
| `--color-sage` | `#879B4A` | New growth | Positive secondary accent, hover detail |
| `--color-teal` | `#2F7770` | Old monitor phosphor | Informational states and data visualization |
| `--color-night` | `#202526` | Unlit console | Dark panels, code blocks, media overlays |
| `--color-white` | `#FFF8E8` | Fresh signal paper | Text on dark or saturated surfaces |

Large surfaces should use one dominant color, one text color, and one supporting accent. Avoid turning every component into a different color block.

### Semantic color roles

Color should communicate function in addition to atmosphere:

```css
:root {
  --surface-page: var(--color-bg-cream);
  --surface-primary: var(--color-orange);
  --surface-secondary: var(--color-yellow);
  --surface-organic: var(--color-green);
  --surface-inverse: var(--color-black);

  --content-primary: var(--color-black);
  --content-inverse: var(--color-bg-cream);
  --content-muted: var(--color-ink-soft);

  --state-success: var(--color-green);
  --state-warning: var(--color-yellow);
  --state-danger: var(--color-rust);
  --state-info: var(--color-teal);
}
```

### Contrast rules

- Use `--color-black` for text on cream, orange, and yellow.
- Use cream or white text on green, night, and rust surfaces.
- Do not use yellow text on cream or orange text on yellow for body copy.
- A color block is not enough to communicate status; pair it with a label, icon, or text.
- Test any new color pairing for readable contrast, especially for small monospace labels.

## 3. Typography

### Type roles

The current site uses a two-part type system:

| Role | Current face | Character |
| --- | --- | --- |
| Display | `Arial Black`, `Impact`, sans-serif | Heavy, compressed, poster-like |
| Interface / body | `Courier New`, Courier, monospace | Terminal, technical, archival |

Recommended fallbacks preserve the intent if the preferred font is unavailable:

```css
:root {
  --font-display: "Arial Black", Impact, Haettenschweiler, sans-serif;
  --font-mono: "Courier New", Courier, monospace;
}
```

### Type scale

Use a compact, high-impact scale. Values are a starting point and can be fluid on smaller screens.

| Token | Size | Line height | Typical use |
| --- | ---: | ---: | --- |
| `--text-xs` | `0.75rem` | `1.2` | Metadata, labels |
| `--text-sm` | `0.9rem` | `1.35` | Navigation, status text |
| `--text-md` | `1rem` | `1.5` | Supporting interface copy |
| `--text-lg` | `1.3rem` | `1.5` | Current body paragraph size |
| `--text-xl` | `2rem` | `1.1` | Secondary headings, large actions |
| `--text-display` | `clamp(2.5rem, 8vw, 4rem)` | `1` | Page and project titles |

### Typography rules

- Display headings are uppercase and may use underscores to reinforce the system identity: `PAPAGEI_BACKEND`.
- Body copy is sentence case, concise, and direct.
- Metadata is uppercase, bold, and monospace.
- Keep letter spacing tight for display headings (`-0.04em` to `-0.08em`); keep monospace labels at normal spacing unless they need extra legibility.
- Use bold weight for body text only when the surrounding surface is busy or the copy is short. Long paragraphs should use a regular weight when available.
- Do not use more than two typefaces or introduce a soft, rounded display face.

### Content examples

```html
<span class="mono-text">&gt; archive_load // FILE_01</span>
<h2>KOTCORE</h2>
<p>A lightweight grid-based engine for building small worlds that keep running.</p>
```

## 4. Geometry, spacing, and depth

### Geometry

The design is deliberately square and assembled rather than polished:

- Border radius: `0` by default.
- Primary border: `4px solid var(--color-black)`.
- Secondary rules: `2px` or `3px` dashed black lines.
- Avoid pills, soft cards, glassmorphism, and large rounded corners.
- If a radius is needed for a native control, keep it subtle (`2px` maximum) and retain the thick border.

### Spacing scale

Use a predictable four-point rhythm:

```css
:root {
  --space-1: 4px;
  --space-2: 8px;
  --space-3: 12px;
  --space-4: 16px;
  --space-5: 20px;
  --space-6: 24px;
  --space-8: 32px;
  --space-10: 40px;
  --space-12: 48px;
  --space-16: 64px;
}
```

Use larger spacing to create a poster-like composition, but keep related metadata and content close together. The current card uses `40px` padding and a `25px` gap below its header.

### Borders and shadows

```css
:root {
  --border-thick: 4px solid var(--color-black);
  --border-medium: 3px solid var(--color-black);
  --border-thin: 2px solid var(--color-black);
  --shadow-neo: 12px 12px 0 var(--color-black);
  --shadow-control: 6px 6px 0 var(--color-black);
}
```

Shadows are hard offsets, never blurred. A component should appear to sit on the page, not float above it. Keep shadow direction consistent: down and to the right.

## 5. Layout principles

### Full-screen sections

The primary composition is a sequence of full-viewport sections:

- Each section is approximately `100vh` tall.
- Content is centered horizontally and vertically.
- Vertical scroll uses mandatory snap points.
- The navigation remains visible as a system header.
- Background media belongs to a section and must never compete with its card.

```css
.section {
  min-height: 100vh;
  display: grid;
  place-items: center;
  padding: var(--space-5);
  scroll-snap-align: start;
}
```

### Card width

Cards should occupy the available width without becoming wall-to-wall:

- Desktop maximum: `800px` for a focused feature card.
- Wide layouts may use a `1200px` container for multiple cards.
- Mobile horizontal padding: at least `16px`.
- Desktop card padding: `40px`; reduce to `24px` on narrow screens.

### Layering

Use layers intentionally:

1. Page texture / paper surface
2. Section media or atmospheric treatment
3. Darkened overlay and pattern
4. Primary card
5. Controls and readable content

Background effects should stay behind content and should not capture pointer events.

## 6. Component library

### 6.1 System navigation

The system navigation is a persistent command strip. It contains a status brand and short section links.

**Anatomy**

- Brand: `SYS.STATUS: [OK]`
- Navigation links: numbered, uppercase, monospace
- Active state: black fill with a green signal color
- Bottom edge: thick black rule

```html
<nav class="sys-nav" aria-label="Primary navigation">
  <div class="nav-brand">SYS.STATUS: [OK]</div>
  <div class="nav-links">
    <a class="nav-link active" href="#welcome">01_INIT</a>
    <a class="nav-link" href="#projects">02_PRJCT</a>
    <a class="nav-link" href="#contact">03_COMMS</a>
  </div>
</nav>
```

**Behavior**

- Active state follows the section in view.
- Hover should visibly change the surface, not only the text color.
- Focus must be visible with keyboard navigation.
- On narrow screens, links may wrap or become a horizontally scrollable strip; do not shrink text until it becomes unreadable.

### 6.2 Neo card

The neo card is the main content container. It is a flat, rectangular slab with a thick outline and offset shadow.

```html
<article class="neo-card bg-orange">
  <div class="card-header">
    <span class="mono-text">&gt; root_access // USER: GUEST</span>
  </div>
  <h1>YAROSLAV_ZGHOBA</h1>
  <p>Developer focused on Kotlin Multiplatform and backend systems.</p>
</article>
```

**Rules**

- Use one background class per card: orange, yellow, green, cream, or a future semantic surface.
- Keep the header rule aligned with the card content.
- Use the shadow only on the outer card, not every nested element.
- A card should have one clear job: introduce, report, present a project, or invite contact.

### 6.3 Card header / system label

The card header is a small piece of system metadata separated from the content by a dashed rule.

```html
<div class="card-header">
  <span class="mono-text">&gt; archive_load // FILE_02</span>
</div>
```

Keep labels short. Prefer a command plus an identifier. The rule is structural, so do not use it as a decorative divider between every paragraph.

### 6.4 Status bar

The status bar communicates a compact pair of facts, usually one technical and one atmospheric.

```html
<div class="status-bar bg-green" role="status">
  <span>SYSTEM: STABLE</span>
  <span>NATURE: 78% COVERAGE</span>
</div>
```

On small screens, allow the values to wrap into a column. Status text should have a textual value such as `STABLE`, `DEGRADED`, or `OFFLINE`; color alone is not sufficient.

### 6.5 Neo button

Buttons are physical controls: thick border, hard shadow, uppercase label, and a pressed state.

```html
<a class="neo-btn bg-green" href="https://example.com">
  PROJECT_DETAILS_&gt;
</a>
```

**States**

| State | Treatment |
| --- | --- |
| Default | Filled surface, black border, `6px` offset shadow |
| Hover | Increase contrast or shift text to the supporting accent |
| Focus | Keep the shadow and add a clear outer focus ring |
| Active | Translate `6px` down/right and remove the shadow |
| Disabled | Reduce contrast and remove pointer affordance; do not rely on opacity alone |

Use a button for an action and a link for navigation. Do not style every text link as a button.

### 6.6 Giant broadcast button

The contact action is an intentionally oversized call to action. It should be used once per major page or flow.

```html
<a class="neo-btn giant-btn bg-orange" href="mailto:yaroslavzghoba@gmail.com">
  [ SEND_E-MAIL ]
</a>
```

The label should describe the result. Good examples include `[ OPEN_CHANNEL ]`, `[ SEND_E-MAIL ]`, and `[ TRANSMIT_MESSAGE ]`.

### 6.7 Project archive card

For project listings, combine an archive label, a short project title, a one-to-three sentence description, metadata, and one action.

```html
<article class="neo-card bg-yellow project-card">
  <div class="card-header">
    <span class="mono-text">&gt; archive_load // FILE_01</span>
  </div>
  <h2>KOTCORE</h2>
  <p>A lightweight 2D grid-based game engine built with Kotlin Multiplatform.</p>
  <ul class="tag-list" aria-label="Technologies">
    <li>KOTLIN</li>
    <li>COMPOSE</li>
    <li>KMP</li>
  </ul>
  <a class="neo-btn bg-green" href="#">PROJECT_DETAILS_&gt;</a>
</article>
```

Tags should be compact and secondary. Avoid making the tag list visually louder than the project title or action.

### 6.8 Media scene

Video, imagery, and atmospheric textures are environmental layers, not primary content.

```html
<div class="bg-video-wrapper" aria-hidden="true">
  <video autoplay loop muted playsinline>
    <source src="media/reclaimed-city.mp4" type="video/mp4" />
  </video>
  <div class="video-overlay"></div>
</div>
```

**Requirements**

- Include `muted` and `playsinline` for predictable autoplay behavior.
- Provide a fallback background color or poster image.
- Pause or reduce motion when the section leaves the viewport.
- Respect `prefers-reduced-motion` by disabling autoplay and transitions.
- Keep the overlay strong enough for text contrast.
- Use `aria-hidden="true"` for purely decorative media.

### 6.9 Reclaimed data panel

For future pages, use a data panel to show metrics, technologies, or system readings.

```html
<section class="data-panel bg-cream">
  <div class="card-header"><span class="mono-text">&gt; telemetry // LIVE</span></div>
  <dl>
    <div><dt>UPTIME</dt><dd>99.98%</dd></div>
    <div><dt>STACK</dt><dd>KOTLIN / KTOR</dd></div>
    <div><dt>THREAT</dt><dd>LOW</dd></div>
  </dl>
</section>
```

Use a data panel when the information is scannable. Use a paragraph when it requires narrative context.

## 7. Interaction and motion

Motion should feel like old machinery starting up: brief, purposeful, and slightly mechanical.

### Timing

```css
:root {
  --duration-fast: 100ms;
  --duration-standard: 200ms;
  --duration-atmospheric: 300ms;
  --ease-mechanical: ease-out;
}
```

- Button press: `100ms`.
- Navigation color change: around `200ms`.
- Media fade: around `300ms`.
- Avoid elastic, bouncing, floating, or glossy transitions.

### Scroll behavior

Scroll snapping is part of the editorial composition, but it must not trap users:

- Keep each section concise enough to scan in one viewport.
- Make keyboard focus targets reachable in the snap container.
- Provide ordinary scrolling when reduced motion is requested.
- Never make essential information available only through an animation.

### Reduced motion

```css
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    scroll-behavior: auto !important;
    transition-duration: 0.01ms !important;
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
  }

  .bg-video-wrapper video {
    display: none;
  }
}
```

## 8. Texture and atmosphere

Texture is a supporting signal of age and environment. Use it sparingly:

- Fine radial dots suggest printed paper or an old display surface.
- Dashed rules suggest patched-together modules.
- Sepia, hue rotation, contrast, and brightness can age media.
- Organic greens should appear as reclaimed growth, not as a generic eco brand.
- Noise must remain subtle enough that body copy stays comfortable to read.

Do not stack multiple high-frequency textures behind small text. If a background is visually active, simplify the card and strengthen its surface color.

## 9. Accessibility and usability

The visual style is expressive, but the system must remain operable:

- Use semantic landmarks: `nav`, `main`, `section`, `article`, and headings in order.
- Every interactive element needs a visible keyboard focus state.
- Maintain a minimum touch target of approximately `44px` for buttons and navigation links.
- Provide meaningful link text; avoid bare `>` or icon-only actions without an accessible name.
- Preserve text contrast on every color surface.
- Do not communicate state through color alone.
- Give decorative media empty alternative text or hide it from assistive technology.
- Ensure horizontal navigation can be reached without a mouse.
- Check the layout at narrow widths and high zoom; long uppercase titles must wrap cleanly.

Suggested focus treatment:

```css
:where(a, button, input, select, textarea):focus-visible {
  outline: 4px solid var(--color-teal);
  outline-offset: 4px;
}
```

## 10. Responsive behavior

### Small screens

- Reduce card padding from `40px` to `24px` or `16px`.
- Let navigation links wrap or scroll horizontally.
- Scale display headings with `clamp()` rather than allowing overflow.
- Stack status-bar values vertically when they no longer fit.
- Keep the hard shadow, but reduce it slightly if it clips at the viewport edge.
- Prefer a static image or flat color when video harms performance.

### Large screens

- Keep the primary card capped around `800px`.
- Use whitespace to make the card feel like a found poster or console panel.
- For multiple projects, use a grid with explicit columns and consistent card heights only when the content length is comparable.

## 11. Voice and content guidelines

### Write like a system that has personality

Good copy is concise, technical, and warm underneath the machinery:

- `Terminal ready for communication.`
- `A lightweight engine for small grid-based worlds.`
- `SYSTEM: STABLE`

Avoid:

- Empty cyberpunk filler: `Welcome to the future of innovation.`
- Excessive jargon that hides the project’s purpose.
- Long blocks of uppercase body copy.
- Alarmist language for ordinary errors.

Use sentence case for descriptions and uppercase only for labels, titles, and intentional system readouts.

## 12. Do and don’t

| Do | Don’t |
| --- | --- |
| Use hard, directional shadows | Use blurred drop shadows |
| Pair saturated fills with black structure | Fill every surface with a different accent |
| Let nature appear through moss colors, texture, and media | Turn the interface into a conventional green sustainability brand |
| Make controls look tactile | Use pill buttons or soft glass panels |
| Use terminal language as an information layer | Replace clear labels with inscrutable symbols |
| Keep motion brief and purposeful | Add bouncing, floating, or perpetual motion |
| Preserve strong contrast and focus states | Sacrifice usability for atmosphere |

## 13. Implementation checklist

Before shipping a new page or component, verify:

- [ ] It uses the established palette or a documented semantic extension.
- [ ] Its geometry is square, bordered, and consistent with the neo-brutalist structure.
- [ ] Its shadow is a hard offset with no blur.
- [ ] Its heading and metadata follow the display/monospace type roles.
- [ ] Its action has a clear label and an appropriate hover, focus, active, and disabled state.
- [ ] Its color contrast is readable on every surface.
- [ ] It works with keyboard navigation and at narrow widths.
- [ ] Decorative media has a fallback and respects reduced motion.
- [ ] Texture supports the hierarchy instead of competing with it.
- [ ] The copy is direct, useful, and consistent with the recovered-system voice.

## 14. Current implementation map

The existing portfolio maps to this system as follows:

| System concept | Current implementation |
| --- | --- |
| System navigation | `.sys-nav`, `.nav-links`, `.nav-link` |
| Full-screen composition | `.scroll-container`, `.section` |
| Neo card | `.neo-card` |
| Card metadata | `.card-header`, `.mono-text` |
| Status readout | `.status-bar` |
| Primary action | `.neo-btn`, `.giant-btn` |
| Palette utilities | `.bg-orange`, `.bg-yellow`, `.bg-green`, `.bg-cream` |
| Atmospheric media | `.bg-video-wrapper`, `.video-overlay` |
| Section awareness | `IntersectionObserver` in `src/main.js` |

This document describes both the current foundation and the intended direction for future components. When extending the site, add new tokens and components here first so the portfolio remains a coherent world rather than a collection of one-off effects.
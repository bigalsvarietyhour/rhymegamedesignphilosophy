# The Rhyme Game · Design System

Companion files:
- `src/theme/index.ts` — typed design tokens (the source of truth for values)
- `docs/design-system.html` — visual reference (open in a browser)

---

## Read this first

Before designing any new screen, answer this question:

> **"Which vocabulary does this screen belong to?"**

The answer decides everything else.

### Gameplay vocabulary

Chunky platform blocks with hard drop shadows. Saturated rhyme colors. Fredoka 20–26px. Used **only** on the actual gameplay grid, the play CTA, and celebration moments.

### Non-gameplay vocabulary

Translucent dark-purple cards (Purple 900 at 40% alpha) on the menu gradient. Fredoka for titles, system sans for descriptions. Used for menus, settings, lists, configuration, stats — everything that isn't the live game.

### The rule

**Never mix the two vocabularies on one screen.** Mixing them creates the cluttered, chaotic feel we're avoiding. Keeping them separate creates clarity — players know what kind of screen they're on the moment it appears.

---

## Philosophy

Three principles guide every design decision. When in doubt, return to these.

1. **Playful, not childish.** We sit between "game" and "tool." Rounded shapes and warm cream surfaces over sterile white. Chunky platforms over flat UI buttons. But never neon overload or cartoon overload — every playful element earns its space.

2. **Color carries meaning.** Every color has a job. Purple is the world. Yellow is celebration. Rhyme colors group sounds. Pink invites creativity. Cream is structural. Never use a color for decoration — if it doesn't communicate, it shouldn't be there.

3. **Everything has physics.** Tappable things are physical objects with weight. Same block, same shadow, same press behavior across the app. Buttons aren't drawings of buttons — they're stylized platforms you can almost touch.

---

## Color system

All values live in `theme.colors`. Never hardcode hex values in components.

### Brand · purple (`theme.colors.purple`)

| Token | Hex | Use |
|---|---|---|
| 50 | `#F3F0FF` | Lightest tint |
| 100 | `#DCD2FF` | |
| 200 | `#B8A4FF` | Caption text on purple backgrounds |
| **400 ★** | `#7B4FFF` | Main brand color (used in mid-gradient) |
| 600 | `#5829E8` | Accent, mid-tones |
| **800 ★** | `#3D1F8F` | Gameplay background bottom stop, dark text |
| 900 | `#2A1466` | Deepest shade; at 40% alpha = translucent card bg |

★ Hero shades. Used most often across the app.

### Brand · yellow (`theme.colors.yellow`)

| Token | Hex | Use |
|---|---|---|
| 50 | `#FFF8DC` | Logo cream / light text on dark surfaces |
| 100–200 | `#FFE99A`–`#FFD960` | Light variants |
| **400 ★** | `#FFC72C` | THE yellow. Primary CTAs, celebration, streaks, one rhyme key |
| 600 | `#E8A800` | Hover/active darker variant |
| 800–900 | `#A66400`–`#5C3700` | Dark text on yellow surfaces |

**Yellow is rare and earns attention.** Use 400 only for: the primary CTA per screen, active toggle/slider states, celebration moments, streak indicators, and one rhyme key. If yellow is on every button, it stops being special.

### Neutral · cream & ink (`theme.colors.neutral`)

Tinted toward purple, never pure gray.

| Token | Hex | Use |
|---|---|---|
| 50 | `#FBF8F0` | Logo cream background |
| **100 ★** | `#EDE4D0` | Non-rhyme block surface in gameplay; secondary menu buttons |
| 200 | `#D4CFC0` | |
| 400 | `#8A7FA8` | |
| 600 | `#4A3D6E` | Secondary text |
| 800 | `#2D1F52` | |
| 900 | `#1A0F3D` | Body text on light surfaces (never use pure black) |

### Rhyme key · gameplay colors (`theme.colors.rhyme`)

Calibrated to equal luminance (~70%) so no color dominates the others. Same hue → same rhyme group.

| Token | Base | Shadow | Text on color |
|---|---|---|---|
| orange | `#F08838` | `#B85A1A` | `#3D1A05` |
| blue | `#4FA8E8` | `#2872A8` | `#0A2E52` |
| yellow | `#FFC72C` | `#C49000` | `#3D2400` |
| green | `#4FCC85` | `#289054` | `#0A3D1F` |

Text on a colored block always uses the darkest stop from that color's own family — never pure black. Pure black on saturated color creates harsh edges; tinted-dark text feels like it belongs.

### Flare zone · pink sunrise gradient (`theme.colors.flare`)

A continuous gradient across 3 cells — hot pink → magenta → lilac. Each cell renders as a `linear-gradient(135deg, start, end)` with its own matching shadow.

| Cell | Start | End | Shadow |
|---|---|---|---|
| 1 | `#FF7DBE` | `#FF6AB8` | `#B83889` |
| 2 | `#FF6AB8` | `#EC6BC4` | `#A8408F` |
| 3 | `#EC6BC4` | `#D070D8` | `#9145A0` |

**Pink is reserved exclusively for the flare zone** — creative invitation moments. Don't use pink for decoration anywhere else. If you find yourself wanting pink for something else, reach for purple or yellow first.

### Semantic · status (`theme.colors.semantic`)

| Token | Hex | Use |
|---|---|---|
| success | `#1F8F5C` | Confirmation, achievement, "go" actions |
| warning | `#E87B00` | Caution (orange, NOT yellow — keeps distinct from brand yellow) |
| error | `#D63848` | Failure, destructive actions, blocking issues |

---

## Background gradients

Every screen uses a vertical purple gradient with the light source at the top.

### Menu gradient (`theme.gradients.menu`)

`linear-gradient(180deg, #6240C8 → #3D1F8F)` — brighter top, energetic. Used on menus, settings, lists, configuration screens — anywhere that isn't the actual game grid.

### Gameplay gradient (`theme.gradients.gameplay`)

`linear-gradient(180deg, #4A2BA8 → #3D1F8F)` — calmer top, focused. Used on the gameplay screen so the player's focus lands on the grid, not the background.

**Both gradients share the same bottom stop (`#3D1F8F`)** — this keeps the bottom of every screen visually consistent, so transitions between menu and gameplay feel like a focusing-in rather than a hard cut.

---

## Typography

Two fonts, two roles. **Don't mix them within a single element.**

### Display: Fredoka (`theme.fonts.display`)

Rounded geometric sans. Used for rhyme words, scores, button labels, screen titles, card titles. Weight 600 (semibold) is the default; weight 700 (bold) only for celebration moments.

Rounded letterforms echo block radius — same "rounded toy" language as the platform blocks.

### Body: System sans (`theme.fonts.body`)

Whatever the OS default is — SF Pro on iOS, Roboto on Android. Used for setting descriptions, supporting captions, paragraphs, metadata.

### Scale (`theme.fontSizes`)

| Token | Size / weight | Use |
|---|---|---|
| `hero` | 32 / 600 Fredoka | Splash titles |
| `xl` | 26 / 600 Fredoka | Gameplay XL, score |
| `lg` | 20 / 600 Fredoka | Rhyme word, button label, screen title |
| `md` | 15 / 600 Fredoka | Card title, setting title |
| `body` | 13 / 400 System | Body, description |
| `caption` | 11 / 500 System uppercase | Section label, meta (with 0.08em letter-spacing) |

---

## Block physics (gameplay vocabulary)

Every tappable platform on a gameplay surface follows these rules. Build one `PlatformBlock` component, reuse everywhere.

### Anatomy

- Border radius: `10px` (`theme.radii.cell`)
- Shadow: `0 4px 0` (no blur, ever)
- Shadow color: same hue as the block, darker (e.g. orange block → `#B85A1A` shadow)
- Text: darkest stop of the block's own color family (never pure black)
- Press behavior: `translateY: 4px` + remove shadow (the block sinks down onto its base)
- Primary CTA variant: bump shadow offset to `5px` for extra emphasis

### React Native shadow note

`box-shadow` doesn't exist in RN. Either:
- iOS: `shadowColor`, `shadowOffset: { width: 0, height: 4 }`, `shadowOpacity: 1`, `shadowRadius: 0`
- Android: `elevation` always blurs, so fake the bottom shadow with a second `<View>` positioned underneath the block. (Recommended for visual consistency across platforms.)

---

## Translucent cards (non-gameplay vocabulary)

Every list item, setting, and configuration row on a non-gameplay surface is one of these. Build one `TranslucentCard` component, reuse everywhere.

### Anatomy

- Background: `rgba(42, 20, 102, 0.4)` — Purple 900 at 40% alpha
- Border radius: `12px` (`theme.radii.card`)
- Padding: `12px 16px`
- Title: Fredoka 15 / 600 in cream `#FFF8DC`
- Description: System sans 11 / 400 in Purple 200 `#B8A4FF`
- **No shadow.** Cards sit *into* the gradient, not on top of it. The translucency does the visual work.

### Layout pattern

Card title and right-side control (toggle, chevron, value badge) sit on one line:

```
┌─────────────────────────────────────────┐
│ Card title                           › │
│ Supporting description                  │
└─────────────────────────────────────────┘
```

Section labels (uppercase caption) sit *above* the card list with `8px` margin below:

```
PLAYBACK
[Card 1]
[Card 2]
[Card 3]
```

---

## Gameplay grid · four cell states

Same physics across all four — only the surface treatment changes.

### Empty beat
Silent rhythm position. Outline + 22% lavender wash. No platform physics — these are slots, not surfaces. Use `theme.cellStates.empty`.

### Non-rhyming word
Cream platform (`#EDE4D0`) with shadow `#B5A88E`. Structural placeholder for words that don't rhyme. Same physics as rhyme blocks — the cream is the only difference. Use `theme.cellStates.nonRhyme`.

### Rhyme word
Colored platform from `theme.cellStates.rhyme` (orange, blue, yellow, green). Hue groups rhymes — same color = same rhyme sound. Tappable for replay/inspection during pauses.

### Flare zone
Pink-sunrise gradient (`theme.cellStates.flare`). Three consecutive cells. Creative invitation — the player adds emphasis or freestyle during these beats.

---

## Spacing & shape

All in `theme.radii` and `theme.spacing`.

| Token | Value | Use |
|---|---|---|
| `radii.cell` | 10px | Gameplay cells |
| `radii.card` | 12px | Translucent cards |
| `radii.button` | 14px | Menu buttons |
| `radii.screen` | 20px | Screen container |
| `spacing.cardGap` | 6–8px | Between translucent cards in a list |
| `spacing.gridGapH` | 8px | Horizontal gap between gameplay cells |
| `spacing.gridGapV` | 10px | Vertical gap (extra room for shadows) |
| `spacing.cardPaddingY/X` | 12px / 16px | Internal card padding |
| `spacing.containerPadding` | 24px | Internal container padding |
| `spacing.screenEdge` | 28px | Screen edge padding |

**Shadow offsets:** 4px default · 5px for primary CTA · always zero blur · no shadow on translucent cards.

---

## Do

- Always use a vertical purple gradient (light from top).
- Use chunky platform blocks **only** on gameplay surfaces and primary CTAs.
- Use translucent cards for everything else (settings, menus, lists).
- Limit yellow to one CTA per screen.
- Use dark-of-own-family for text on colored backgrounds.
- Reserve pink for creative moments only.
- Dock primary actions at the bottom of the screen.
- Reference `theme.*` tokens — never hardcode hex values or sizes.

## Don't

- Mix the two vocabularies on one screen.
- Use flat purple backgrounds — always gradient.
- Use pure black for text — always tint toward purple.
- Use pure white — use cream instead.
- Mix Fredoka and system font in one element.
- Add new brand colors. Two hues only.
- Use blurred shadows. Always hard, zero blur.
- Float buttons over content. Dock them.
- Stack multiple yellow CTAs on one screen.

---

## One-line summary

Two brand colors, two vocabularies (platform blocks for gameplay, translucent cards for everything else), rounded geometric type. Color carries meaning, never decoration. Everything you can tap is a physical object with weight.

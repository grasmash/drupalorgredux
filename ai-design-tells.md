# AI-Generated Design Tells & Fixes

Research compiled 2026-03-23.

---

## Part 1: Visual Patterns That Scream "AI Made This"

### The "AI Starter Pack" (instantly recognizable)
- **Purple-to-blue/indigo gradients** — the single biggest tell. Traced back to Tailwind's `bg-indigo-500` being used in every demo; LLMs absorbed it as "modern." Adam Wathan publicly apologized for this in Aug 2025.
- **Inter font everywhere** — it's the statistical default. Safe, clean, soulless.
- **Three icon boxes in a row** — the holy trinity of AI layout: three equal-width cards with an icon, heading, and short paragraph. Every AI landing page has this.
- **Glassmorphism / frosted glass cards** — semi-transparent cards with `backdrop-filter: blur()` floating on pastel gradient backgrounds.
- **3D abstract blob humans** — faceless illustrated characters in impossible poses holding glowing orbs.
- **Perfectly symmetrical grids** — everything snaps to a rigid 12-column grid with identical spacing. No element dares break the pattern.
- **Timid, muted color palettes** — safe neutrals with one accent color (usually indigo/violet). No bold choices.
- **Overly uniform border-radius** — same `rounded-xl` or `rounded-2xl` on every single element.
- **Generic hero section** — big headline, sub-headline, two buttons (one filled, one outlined), gradient background. Every. Single. Time.
- **Stock-photo-quality AI images** — hyper-polished, emotionally empty, ethnically ambiguous people smiling at laptops.

### Content Patterns
- Padding content that restates the same point three ways without advancing an argument.
- Buzzword-heavy headings: "Revolutionize," "Seamlessly," "Unlock the Power of."
- Every section follows the same rhythm: heading, paragraph, CTA. No variation.
- Perfect grammar with zero personality or voice.

---

## Part 2: Specific CSS/Design Fixes

### Kill the purple
```css
/* DON'T: the AI default */
background: linear-gradient(135deg, #6366f1, #8b5cf6);

/* DO: pick a palette that isn't indigo/violet */
/* Use OKLCH color space for perceptually uniform ramps */
--primary: oklch(55% 0.15 250); /* example: a real teal */
```
Define your own theme tokens (`--primary`, `--surface`, `--text`) instead of relying on Tailwind defaults. If using Tailwind, override the default palette in `tailwind.config` before writing any components.

### Break the grid symmetry
```css
/* DON'T: perfectly equal three-column grid */
grid-template-columns: 1fr 1fr 1fr;

/* DO: intentional asymmetry */
grid-template-columns: 1.2fr 0.8fr 1fr;
/* Or use varied card sizes, spanning, offset items */
```
Let some elements break the grid. Offset an image so it overlaps a section boundary. Let whitespace be uneven on purpose.

### Vary border-radius
```css
/* DON'T: same radius on everything */
border-radius: 1rem; /* on cards, buttons, inputs, images... */

/* DO: different radii for different elements */
--radius-button: 6px;
--radius-card: 12px;
--radius-avatar: 50%;
--radius-image: 2px; /* or 0 */
```

### Add texture and grain
```css
/* Subtle noise overlay to kill the "too clean" feel */
.section::after {
  content: '';
  position: absolute;
  inset: 0;
  background-image: url('/noise.svg'); /* or a tiny noise PNG */
  opacity: 0.03;
  pointer-events: none;
  mix-blend-mode: overlay;
}
```
Even 2-5% opacity noise on backgrounds breaks the sterile digital feel.

### Typography that isn't Inter
- Pick a font with actual character: a serif for headings (e.g., Fraunces, Playfair Display, Lora), a humanist sans for body (e.g., Source Sans, Nunito, Atkinson Hyperlegible).
- Vary font sizes non-linearly. AI tends to use a perfectly calculated type scale. Real designs have sizes that "feel right" rather than follow a strict ratio.
- Use tighter letter-spacing on large headings, looser on small text. AI often leaves defaults.

### Ditch the safe spacing
```css
/* DON'T: uniform section padding */
section { padding: 5rem 0; }

/* DO: varied, intentional spacing */
.hero { padding: 8rem 0 4rem; }
.features { padding: 3rem 0 6rem; }
.testimonials { padding: 5rem 0 2rem; }
```
Real designs breathe unevenly. Dense where content demands it, expansive where you want pause.

### Use real shadows, not the default
```css
/* DON'T: Tailwind shadow-lg on everything */
box-shadow: 0 10px 15px -3px rgb(0 0 0 / 0.1);

/* DO: layered, colored shadows */
box-shadow:
  0 1px 2px oklch(30% 0.02 250 / 0.06),
  0 4px 8px oklch(30% 0.02 250 / 0.04),
  0 12px 24px oklch(30% 0.02 250 / 0.03);
```
Colored shadows (tinted toward the background or brand color) look significantly more polished than gray.

### Avoid the two-button hero
```css
/* The AI classic: */
/* [Get Started]  [Learn More →] */
/* One filled primary, one ghost/outlined. Every time. */
```
Use a single CTA, or a CTA + inline text link, or a CTA + social proof element. Anything but the filled + outlined button duo.

---

## Part 3: What Hand-Crafted Sites Do Differently

1. **Imperfection is intentional.** Hand-drawn elements, slightly rough edges, texture overlays (grain, paper, subtle noise), ink-bleed effects. The 2026 trend is explicitly anti-AI: scribble accents, handwriting fonts, retro details.

2. **Layouts have personality.** Elements overlap. Images bleed to edges. Sections have different visual treatments instead of alternating white/gray backgrounds. Negative space is used confidently and unevenly.

3. **Custom illustrations over stock.** Even simple custom SVG illustrations with a consistent style beat any AI-generated or stock imagery. They signal "someone made choices here."

4. **Content has voice.** Short sentences. Sentence fragments. Opinions. Humor. Specific details instead of generalities. Real customer names and photos instead of "John D. - CEO."

5. **Interaction design has friction.** Not everything loads instantly with a smooth fade-in. Some elements have deliberate, surprising animations. Hover states do something unexpected. Scroll interactions are bespoke, not a library default.

6. **Color choices are opinionated.** Hand-crafted sites pick a palette and commit. Unexpected color pairings (olive + coral, navy + peach). High contrast where it matters. They don't hedge with safe neutrals.

7. **Typography is curated.** Font pairing is deliberate (a display font with character + a workhorse body font). Headings might be set in all-caps with wide tracking, or oversized and cropped. There's a visible typographic hierarchy beyond just size changes.

8. **Details at the micro level.** Custom list bullets. Styled blockquotes. Unique link hover effects. Custom scrollbar styling. Favicon that matches the brand. These details compound into a sense of craft.

9. **Photography is real.** Actual photos of actual people, products, and spaces — even if imperfect. A slightly grainy behind-the-scenes photo signals authenticity more than a perfect AI render.

10. **The site doesn't try to look like everything.** The strongest tell of human design is a point of view: the site looks like *itself*, not like the statistical average of all websites.

---

## Quick Checklist: De-AI-ify Your Site

- [ ] No purple/indigo gradients (unless it's genuinely your brand color)
- [ ] Not using Inter/system-ui as primary font
- [ ] No three-equal-cards-with-icons section
- [ ] Hero section doesn't have filled + ghost button combo
- [ ] Border radius varies across element types
- [ ] At least one section breaks the grid or uses asymmetry
- [ ] Background has subtle texture/grain (not flat solid colors)
- [ ] Shadows are layered and color-tinted
- [ ] Section spacing is intentionally uneven
- [ ] Copy has a distinct voice (not "Unlock the power of...")
- [ ] Custom or real imagery (no AI-generated people)
- [ ] At least one surprising or non-standard design detail

---

Sources:
- [Why Your AI Keeps Building the Same Purple Gradient Website](https://prg.sh/ramblings/Why-Your-AI-Keeps-Building-the-Same-Purple-Gradient-Website)
- [AI Purple Problem: Make Your UI Unmistakable (DEV Community)](https://dev.to/jaainil/ai-purple-problem-make-your-ui-unmistakable-3ono)
- [How to Break the AI-Generated UI Curse (DEV Community)](https://dev.to/a_shokn/how-to-break-the-ai-generated-ui-curse-your-guide-to-authentic-professional-design-2en)
- [Why Your AI-Generated UI Looks Like Everyone Else's (Medium)](https://medium.com/@Rythmuxdesigner/why-your-ai-generated-ui-looks-like-everyone-elses-and-how-to-break-the-pattern-7a3bf6b070be)
- [How to Identify AI-Generated Websites (Originality.AI)](https://originality.ai/blog/how-to-identify-ai-generated-websites)
- [Avoid Generic AI Website Content (Wix)](https://www.wix.com/blog/avoid-generic-ai-website-content)
- [Design Trends 2026: Imperfection, Rebellion, and Human Work](https://lindsaymarsh.substack.com/p/design-trends-2026-imperfection-rebellion)
- [Aesthetics in the AI Era: Visual + Web Design Trends for 2026](https://aigoodies.beehiiv.com/p/aesthetics-2026)
- [Web Design Trends to Expect in 2026 (Elementor)](https://elementor.com/blog/web-design-trends-2026/)

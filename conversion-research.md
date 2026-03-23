# Landing Page Conversion Research for Open Source Software Projects

Research compiled March 2026. Based on industry data, the Evil Martians study of 100+ dev tool landing pages, and direct analysis of Laravel, Supabase, Next.js, Tailwind CSS, and Vercel homepages.

---

## 1. What Should Be Above the Fold?

Users spend 10-20 seconds evaluating a homepage before deciding to stay. The hero must do its job in 3 seconds or the rest of the page is irrelevant.

**The winning formula (used by ~90% of top dev tool pages):**

- **Centered headline** (under 8 words / 44 characters max). No jargon.
- **One-line subheadline** explaining what the product does and for whom.
- **Two CTAs side by side**: one primary action ("Start your project," "Get started," "Deploy on Cloud") and one secondary/low-commitment ("View docs," "GitHub," "Learn more").
- **Visual element directly below the headline**: product screenshot, animated UI, code snippet, or interactive embed.
- **Optional eyebrow text** above the headline for announcements (new release, funding, event).

**What NOT to put above the fold:**
- Navigation-heavy headers with too many links
- Vague aspirational statements without specifics ("Unlock the future of...")
- Feature lists (save for below)
- Video that auto-plays

**Real examples:**
- Laravel: "The clean stack for Artisans and agents." + "Deploy on Cloud" / "View framework docs"
- Supabase: "Build in a weekend, Scale to millions" + "Start your project" / "Request a demo"
- Next.js: "The React Framework for the Web" + "Get Started" / "Learn Next.js"
- Tailwind: "Rapidly build modern websites without ever leaving your HTML." + "Get started"

---

## 2. Optimal Section Ordering

The proven sequence follows a psychological narrative: **Motivate, Assure, Prompt** (MAP framework).

**Standard high-converting order:**

| # | Section | Purpose |
|---|---------|---------|
| 1 | Hero (headline + CTA + visual) | Hook and orient in 3 seconds |
| 2 | Trust bar (logos or metrics) | Immediate credibility |
| 3 | Primary feature story (2-4 features) | Show core value / how it works |
| 4 | Secondary features or integrations | Breadth of capability |
| 5 | Social proof (testimonials) | Third-party validation |
| 6 | Getting started / templates / quickstart | Reduce perceived effort |
| 7 | Final CTA (big, full-width) | Last conversion opportunity |
| 8 | Footer | Navigation, legal, secondary links |

**Observed section counts from real pages:**
- Laravel: 8 sections before footer (hero, framework overview, cloud, preview envs, monitoring, frontend, CTA, testimonials, events)
- Supabase: ~10 sections (hero, logos, 7 product features, frameworks, customer stories, templates, dashboard, community, open source, final CTA)
- Next.js: 7 sections (hero, features grid, foundation/tooling, templates, social proof, feature highlights, footer)
- Tailwind: 8 sections (hero, featured content, sponsors, "why Tailwind" demos, performance, showcase, Tailwind Plus, footer)

---

## 3. CTA Strategy: How Many and Where

**The rule: One GOAL, repeated 3 times. Never multiple competing goals.**

Reducing competing CTAs to a single goal increased conversions by 266% in one study. But repeating that same CTA throughout a long page outperforms a single placement.

**Optimal CTA placement pattern:**

1. **Hero section** (above the fold) -- primary + secondary CTA
2. **Mid-page** (after 2-3 feature sections) -- repeat primary CTA
3. **Final section** (pre-footer) -- full-width, visually distinct CTA block

**CTA copy that works for dev tools:**
- Primary: Action-specific verbs ("Start building," "Deploy now," "Get started")
- Secondary: Low-commitment ("Read the docs," "View on GitHub," "See examples")
- Avoid generic: "Learn more," "Submit," "Click here"

**What the best pages do:**
- Laravel: CTAs in hero, after each product section, and a dedicated full-width CTA section before testimonials
- Supabase: "Start your project" / "Request a demo" in hero, repeated in final section
- Vercel: "Start Deploying" in hero, mid-page, and footer

---

## 4. Social Proof: Role and Placement

Social proof influences 90% of buying decisions. Testimonials can increase conversions by 34%. Enterprise client logos increased one company's conversions by 260%.

**Two distinct types, placed differently:**

### Trust Bar (logos/metrics) -- Place IMMEDIATELY after hero
- For B2B/enterprise: Recognizable customer logos (50% use auto-scrolling carousels)
- For developer/individual tools: GitHub stars, download counts, npm installs, awards
- Supabase: Scrolling carousel of 16+ logos (Mozilla, GitHub, 1Password, PwC) directly under hero
- Vercel: Customer logos with specific performance metrics ("build times went from 7m to 40s")

### Testimonials -- Place AFTER feature sections (lower half of page)
- Nearly all top dev tool pages use **curated** testimonials, not auto-pulled tweets
- Include: quote, real name, title, company, headshot
- Quantitative testimonials outperform vague praise (quote with specific metric showed 35% conversion lift vs. logos alone)
- Laravel: 7 testimonials with photos, names, and titles, placed after all product sections
- Next.js: Company logos + 3 detailed testimonials in lower third of page

**Early-stage projects without big-name users:**
- Show a single testimonial with a client photo
- Display GitHub stars, contributor count, or download stats
- "Ask your first client, a teammate, or even a friend to write one sentence about the product. That's enough." (Evil Martians)

---

## 5. Should "Try It Now" Be Above or Below Features?

**Above the fold, always.** But also repeat it below.

For developer tools specifically, the primary CTA should be in the hero because:
- Developers who already know the product want to jump straight in
- Returning visitors should not have to scroll to find the action
- Quick decision-makers convert from the hero; researchers convert from the repeated CTA below

However, for **complex products** where the value proposition isn't immediately obvious, the repeated CTA after feature explanations will capture the majority of conversions. The hero CTA catches the already-convinced; the mid-page and final CTAs catch those who needed persuading.

**The data:** Long-form pages with multiple CTA placements produce more leads than pages with only an above-the-fold CTA.

---

## 6. How Much Content Before the First CTA?

**Zero.** The first CTA should be in the hero section itself, before any feature content.

The hero formula is:
1. Headline (5-8 words)
2. Subheadline (1 sentence)
3. CTA buttons (immediately)
4. Visual element (below the CTAs)

That means the visitor sees a CTA within the first 3 seconds, with roughly 20-30 words of content preceding it. Every page analyzed (Laravel, Supabase, Next.js, Tailwind, Vercel) places the CTA directly in the hero with minimal preceding text.

**Do not** make the visitor scroll to find the first CTA. Do not put a features section, testimonial, or explanation before the first opportunity to convert.

---

## 7. Ideal Number of Sections

There is no universal magic number, but the data clusters around **6-10 sections** before the footer.

**Breakdown by page type:**
- **Focused single-product pages** (Tailwind, Next.js): 6-8 sections
- **Platform/multi-product pages** (Supabase, Laravel, Vercel): 8-12 sections

**The guiding principle:** Every section must earn its place by either building belief or removing a specific objection. Cut any section that doesn't do one of those two things.

**Must-have sections (6 minimum):**
1. Hero
2. Trust bar
3. Core features / how it works
4. Extended features or use cases
5. Social proof
6. Final CTA

**Optional but valuable:**
- Integrations/compatibility logos
- Getting started / quickstart guide
- Comparison table (only in competitive markets)
- FAQ (placed near bottom, accordion style)
- Community / open source section
- Blog/changelog preview (signals active development)
- Pricing (most dev tool pages defer this to a separate page)

---

## 8. Product Demo/Screenshot vs. Value Prop First?

**Lead with the value proposition. Show the product simultaneously or immediately below.**

The winning pattern for developer tools is: headline states the value prop, visual element directly below demonstrates the product. They are not sequential -- they are paired.

**Effective visual approaches (from Evil Martians research, strongest first):**
1. **Animated product UI** -- Shows the product in action, multiple surfaces
2. **Code snippets** -- Common for libraries/SDKs (Tailwind does this well)
3. **Static product screenshot** -- Fast to implement, still builds confidence (Linear)
4. **Switchable UI tabs** -- For products with multiple use cases
5. **Live embed** -- Best for narrow-scope tools (image editors, formatters)

**Developer-specific insight:** Developers want to see how it works on the homepage itself. Step 1, Step 2, Step 3, Success patterns are highly effective. In-place code examples that show input/output without navigating away are particularly strong.

**Do NOT:**
- Lead with an abstract illustration or stock imagery
- Hide the product behind a "Watch demo" button
- Show the product without context for what problem it solves
- Use only a screenshot with no value prop text

---

## 9. What Kills Conversion? Common Mistakes

### Fatal mistakes (each proven to measurably reduce conversion):

1. **Slow load times.** At 3 seconds, bounce rate hits 32%. At 5 seconds, 90%. Every additional second costs ~7% conversion.

2. **Vague hero headline.** If a visitor can't understand what your product does in 5 seconds, they leave. "Unlock your potential" tells them nothing.

3. **Multiple competing CTAs.** "Sign up," "Watch demo," "Read blog," "Join Discord" all fighting for attention. One goal per page.

4. **No social proof.** No logos, no testimonials, no star counts = no trust. Even one testimonial is better than none.

5. **Cluttered design.** Too many colors, too many animations, too much text. Clean, minimal layouts with breathing room outperform busy ones consistently.

6. **Poor mobile experience.** 60%+ of traffic is mobile, but desktop converts 8% better -- the gap is caused by poor mobile optimization, not inherent mobile disadvantage.

7. **Salesy language.** Developer audiences are particularly allergic to marketing speak. "Revolutionary AI-powered paradigm shift" will lose developers instantly. Be direct and specific.

8. **Message mismatch.** If the referring link/ad/tweet promises one thing and the landing page says another, conversion drops immediately.

9. **Asking too much upfront.** Long forms, required account creation before seeing value, mandatory email for docs access. Short forms win. Reduce friction to zero where possible.

10. **No clear visual hierarchy.** If everything is bold, nothing is bold. The eye needs a clear path: headline, subheadline, CTA, visual, scroll.

11. **Hiding the CTA.** Placing the first CTA below the fold, using the same color as the background, or making it look like body text.

12. **No final CTA.** The pre-footer CTA block is your last chance to convert someone who read the whole page. Make it big, visually distinct, and clear.

---

## 10. How the Best Open Source Pages Structure Their Content

### Laravel (laravel.com)
| Order | Section | Content |
|-------|---------|---------|
| 1 | Hero | "The clean stack for Artisans and agents" + 2 CTAs |
| 2 | Framework overview | Features list + code tabs + feature icons |
| 3 | Laravel Cloud | Deployment platform pitch + CTA |
| 4 | Preview environments | PR review feature + CTA |
| 5 | Nightwatch | Monitoring product + CTA |
| 6 | Frontend integration | React/Vue/Svelte support + code tabs |
| 7 | Full-width CTA | "Create without limits. What will you ship?" + 2 CTAs |
| 8 | Testimonials | 7 quotes with photos, names, titles |
| 9 | Events | Community events + ticket CTAs |

**Pattern:** Hero, then product-by-product showcase (each with its own CTA), then social proof, then community. No trust bar -- relies on 84K GitHub stars in the nav.

### Supabase (supabase.com)
| Order | Section | Content |
|-------|---------|---------|
| 1 | Hero | "Build in a weekend, Scale to millions" + 2 CTAs |
| 2 | Logo trust bar | 16+ scrolling company logos |
| 3 | Product features | 7 individual feature cards (DB, Auth, Functions, Storage, Realtime, Vector, APIs) |
| 4 | Framework quickstarts | 9 framework logos with links |
| 5 | Customer stories | Case study carousel |
| 6 | Templates | Quick-start templates |
| 7 | Dashboard features | Table editor, SQL editor, RLS |
| 8 | Community | Discord + curated tweets |
| 9 | Open source | Transparency messaging + GitHub link |
| 10 | Final CTA | Repeat of hero CTAs |

**Pattern:** Classic trust-first approach. Logos immediately after hero. Product features with breadth. Community and open source emphasis at the bottom. Final CTA mirrors the hero.

### Next.js (nextjs.org)
| Order | Section | Content |
|-------|---------|---------|
| 1 | Hero | "The React Framework for the Web" + 2 CTAs + npx command |
| 2 | Features grid | 8 features in responsive grid |
| 3 | Foundation | Powered by React, Turbopack, SWC |
| 4 | Templates | Tab selector with template previews + Deploy CTA |
| 5 | Social proof | Company logos + 3 testimonials |
| 6 | Feature highlights | 3 cards (optimizations, streaming, v16) |

**Pattern:** Compact and focused. Features before social proof. Template/getting-started section drives deployment action. Testimonials placed after core value is established.

### Tailwind CSS (tailwindcss.com)
| Order | Section | Content |
|-------|---------|---------|
| 1 | Hero | Headline + "Get started" CTA |
| 2 | Featured content | Book/resource promotion |
| 3 | Sponsors | 43+ sponsor logos |
| 4 | Why Tailwind | 12 interactive feature demos |
| 5 | Performance | Build size/speed demonstration |
| 6 | Showcase | 15+ company logos using Tailwind |
| 7 | Tailwind Plus | Commercial product upsell |

**Pattern:** Leads with sponsors instead of customer logos (open source funding model). Massive interactive demo section is the centerpiece. Social proof comes late, after the product has demonstrated itself through live examples.

### Vercel (vercel.com)
| Order | Section | Content |
|-------|---------|---------|
| 1 | Hero | "Build and deploy on the AI Cloud" + 2 CTAs |
| 2 | Social proof with metrics | Customer logos + specific performance numbers |
| 3 | Use cases | AI Apps, Web Apps, Ecommerce, Marketing, Platforms |
| 4 | Features | Agents, Fluid Compute, AI Gateway with code samples |
| 5 | Templates | Framework options + Deploy CTA |
| 6 | Footer CTAs | "Talk to an Expert" / "Get an Enterprise Trial" |

**Pattern:** Enterprise-focused. Social proof with quantitative metrics immediately after hero. Organized by use case rather than feature. Final CTAs shift to enterprise (demo/trial) rather than self-serve.

---

## Summary: The Playbook

1. **Hero:** Short headline + one-line description + 2 CTAs (action + docs) + product visual. All above the fold.
2. **Trust:** Logos or metrics immediately after hero. Use whatever you have -- stars, downloads, user count, or even one testimonial.
3. **Features:** 2-4 core capabilities, shown through code examples, screenshots, or interactive demos. Problem-oriented framing beats feature lists.
4. **Extended value:** Integrations, use cases, or additional product areas.
5. **Social proof:** Curated testimonials with names, titles, photos. Quantitative beats qualitative.
6. **Getting started:** Templates, quickstart, or framework support. Reduce perceived effort.
7. **Final CTA:** Full-width, visually distinct block. Repeat the hero CTA. Make it impossible to miss.
8. **Total sections:** 6-10. Every section earns its place or gets cut.

---

## Sources

- [Evil Martians: We Studied 100 Dev Tool Landing Pages](https://evilmartians.com/chronicles/we-studied-100-devtool-landing-pages-here-is-what-actually-works-in-2025)
- [Webstacks: SaaS Website Conversions 2026](https://www.webstacks.com/blog/website-conversions-for-saas-businesses)
- [Fibr: SaaS Landing Pages Best Practices 2026](https://fibr.ai/landing-page/saas-landing-pages)
- [Unbounce: State of SaaS Landing Pages](https://unbounce.com/conversion-rate-optimization/the-state-of-saas-landing-pages/)
- [CXL: How to Build a High-Converting Landing Page](https://cxl.com/blog/how-to-build-a-high-converting-landing-page/)
- [CXL: Above the Fold](https://cxl.com/blog/above-the-fold/)
- [Instapage: CTA Above or Below Fold](https://instapage.com/blog/call-to-action-above-or-below-fold/)
- [LandingPageFlow: CTA Placement Strategies 2026](https://www.landingpageflow.com/post/best-cta-placement-strategies-for-landing-pages)
- [Linear Design: Ideal Landing Page Layout](https://lineardesign.com/blog/landing-page-layout/)
- [Magic UI: 13 Essential Landing Page Sections](https://magicui.design/blog/landing-page-sections)
- [Thrive Agency: 10 Landing Page Mistakes](https://thriveagency.com/news/10-landing-page-mistakes-that-kill-conversions-and-how-to-fix-them/)
- [WiserNotify: 25 CTA Statistics 2026](https://wisernotify.com/blog/call-to-action-stats/)
- [MailerLite: Social Proof Examples for Landing Pages](https://www.mailerlite.com/blog/social-proof-examples-for-landing-pages)
- [KlientBoost: Landing Page Testimonials](https://www.klientboost.com/landing-pages/landing-page-testimonials/)
- [Markepear: Dev Tool Landing Page Examples](https://www.markepear.dev/examples/landing-page)
- [Webflow: Homepage Optimization Strategies](https://webflow.com/blog/homepage-optimization-strategies)

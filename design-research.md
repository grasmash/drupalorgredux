# Modern Web Design Research: Landing Page Techniques (2025-2026)

Compiled research of implementable CSS/JS techniques for a modern marketing landing page.
Focus: vanilla CSS and minimal JS, no frameworks.

---

## Table of Contents

1. [Scroll-Triggered Animations](#1-scroll-triggered-animations)
2. [Micro-Interactions](#2-micro-interactions)
3. [Loading & Entrance Animations](#3-loading--entrance-animations)
4. [Modern CSS Effects](#4-modern-css-effects)
5. [Text Effects](#5-text-effects)
6. [Navigation Patterns](#6-navigation-patterns)
7. [Hero Section Patterns](#7-hero-section-patterns)
8. [Card & Grid Interactions](#8-card--grid-interactions)
9. [Performance](#9-performance)

---

## 1. Scroll-Triggered Animations

### 1a. IntersectionObserver -- Fade/Slide In on Scroll

The foundational pattern for scroll-triggered reveals. Add a class when elements enter the viewport.

```css
/* Base state: hidden */
.reveal {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.6s ease, transform 0.6s ease;
}

/* Revealed state */
.reveal.is-visible {
  opacity: 1;
  transform: translateY(0);
}

/* Directional variants */
.reveal--left {
  transform: translateX(-30px);
}
.reveal--left.is-visible {
  transform: translateX(0);
}

.reveal--right {
  transform: translateX(30px);
}
.reveal--right.is-visible {
  transform: translateX(0);
}

.reveal--scale {
  transform: scale(0.95);
}
.reveal--scale.is-visible {
  transform: scale(1);
}
```

```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach((entry) => {
    if (entry.isIntersecting) {
      entry.target.classList.add('is-visible');
      observer.unobserve(entry.target); // Only animate once
    }
  });
}, {
  threshold: 0.15,
  rootMargin: '0px 0px -50px 0px'
});

document.querySelectorAll('.reveal').forEach((el) => {
  observer.observe(el);
});
```

### 1b. CSS Scroll-Driven Animations (No JS Required)

Native CSS approach using `animation-timeline`. Supported in Chrome 115+, Edge 115+.

**Fade in on scroll into view:**
```css
@keyframes fade-in {
  from {
    opacity: 0;
    transform: translateY(40px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.scroll-reveal {
  animation: fade-in linear both;
  animation-timeline: view();
  animation-range: entry 0% entry 100%;
}
```

**Animate in AND out as element enters/exits viewport:**
```css
@keyframes animate-in-and-out {
  entry 0% {
    opacity: 0;
    transform: translateY(100%);
  }
  entry 100% {
    opacity: 1;
    transform: translateY(0);
  }
  exit 0% {
    opacity: 1;
    transform: translateY(0);
  }
  exit 100% {
    opacity: 0;
    transform: translateY(-100%);
  }
}

.scroll-animate {
  animation: linear animate-in-and-out;
  animation-timeline: view();
}
```

**Reading progress bar (scroll-linked):**
```css
@keyframes grow-progress {
  from { transform: scaleX(0); }
  to { transform: scaleX(1); }
}

.progress-bar {
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 3px;
  background: var(--color-primary, #6200ee);
  transform-origin: 0 50%;
  animation: grow-progress auto linear;
  animation-timeline: scroll();
  z-index: 1000;
}
```

### 1c. Parallax with Scroll-Driven CSS Animations

No JS needed -- pure CSS parallax via `animation-timeline: scroll()`.

```css
@keyframes parallax-bg {
  from { background-position: center 0px; }
  to { background-position: center -400px; }
}

.parallax-section {
  background-image: url('hero-bg.jpg');
  background-size: cover;
  animation: parallax-bg linear;
  animation-timeline: scroll();
}

/* Parallax for floating elements at different speeds */
@keyframes float-slow {
  from { transform: translateY(0); }
  to { transform: translateY(-100px); }
}

@keyframes float-fast {
  from { transform: translateY(0); }
  to { transform: translateY(-250px); }
}

.parallax-layer--slow {
  animation: float-slow linear;
  animation-timeline: scroll();
}

.parallax-layer--fast {
  animation: float-fast linear;
  animation-timeline: scroll();
}
```

### 1d. Section-Based Scroll Progress with View Timeline

Animate a progress indicator per section using named view timelines.

```css
@property --progress {
  syntax: "<number>";
  inherits: true;
  initial-value: 0;
}

@keyframes track-section {
  from { --progress: 0; }
  to { --progress: 1; }
}

section {
  animation-timeline: view(block 98% 2%);
  animation-name: track-section;
  animation-fill-mode: both;
}

/* Child indicator bar scales based on parent's --progress */
section .indicator-bar {
  transform: scaleY(var(--progress));
  transform-origin: top;
  background: var(--color-primary);
  width: 4px;
  height: 100%;
}
```

---

## 2. Micro-Interactions

### 2a. Material Design Ripple Effect

Click ripple that expands from the click point.

```css
.ripple-btn {
  position: relative;
  overflow: hidden;
  cursor: pointer;
  /* your button styles */
}

.ripple-btn .ripple {
  position: absolute;
  border-radius: 50%;
  transform: scale(0);
  animation: ripple-expand 600ms linear;
  background-color: rgba(255, 255, 255, 0.4);
  pointer-events: none;
}

@keyframes ripple-expand {
  to {
    transform: scale(4);
    opacity: 0;
  }
}
```

```javascript
function createRipple(event) {
  const button = event.currentTarget;
  const circle = document.createElement('span');
  const diameter = Math.max(button.clientWidth, button.clientHeight);
  const radius = diameter / 2;

  circle.style.width = circle.style.height = `${diameter}px`;
  circle.style.left = `${event.offsetX - radius}px`;
  circle.style.top = `${event.offsetY - radius}px`;
  circle.classList.add('ripple');

  // Remove existing ripple
  const existing = button.querySelector('.ripple');
  if (existing) existing.remove();

  button.appendChild(circle);
  circle.addEventListener('animationend', () => circle.remove());
}

document.querySelectorAll('.ripple-btn').forEach((btn) => {
  btn.addEventListener('click', createRipple);
});
```

### 2b. Magnetic Button Effect

Button subtly follows the cursor when nearby, creating a magnetic pull.

```css
.magnetic-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 16px 40px;
  font-size: 1.125rem;
  font-weight: 600;
  border-radius: 999px;
  border: none;
  cursor: pointer;
  background: var(--color-primary, #1f1f1f);
  color: #fff;
  transition: transform 0.25s ease-out;
  will-change: transform;
}
```

```javascript
document.querySelectorAll('.magnetic-btn').forEach((btn) => {
  btn.addEventListener('mousemove', (e) => {
    const rect = btn.getBoundingClientRect();
    const centerX = rect.left + rect.width / 2;
    const centerY = rect.top + rect.height / 2;
    const deltaX = e.clientX - centerX;
    const deltaY = e.clientY - centerY;
    const distance = Math.sqrt(deltaX ** 2 + deltaY ** 2);
    const maxDistance = 120;

    if (distance < maxDistance) {
      btn.style.transform = `translate(${deltaX * 0.25}px, ${deltaY * 0.25}px)`;
    }
  });

  btn.addEventListener('mouseleave', () => {
    btn.style.transform = 'translate(0, 0)';
  });
});
```

### 2c. Button Hover Effects (Pure CSS)

```css
/* Fill from left */
.btn-fill {
  position: relative;
  overflow: hidden;
  z-index: 1;
  transition: color 0.4s ease;
}
.btn-fill::before {
  content: '';
  position: absolute;
  inset: 0;
  background: var(--color-primary);
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  z-index: -1;
}
.btn-fill:hover::before {
  transform: scaleX(1);
}
.btn-fill:hover {
  color: #fff;
}

/* Shine/gloss sweep */
.btn-shine {
  position: relative;
  overflow: hidden;
}
.btn-shine::after {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    120deg,
    transparent 30%,
    rgba(255, 255, 255, 0.3) 50%,
    transparent 70%
  );
  transition: left 0.6s ease;
}
.btn-shine:hover::after {
  left: 100%;
}

/* Border draw on hover */
.btn-border-draw {
  position: relative;
  background: transparent;
  border: 2px solid transparent;
  padding: 12px 32px;
}
.btn-border-draw::before,
.btn-border-draw::after {
  content: '';
  position: absolute;
  width: 0;
  height: 0;
  border: 2px solid transparent;
  transition: all 0.35s ease;
}
.btn-border-draw::before {
  top: 0;
  left: 0;
}
.btn-border-draw::after {
  bottom: 0;
  right: 0;
}
.btn-border-draw:hover::before {
  width: 100%;
  height: 100%;
  border-top-color: var(--color-primary);
  border-right-color: var(--color-primary);
}
.btn-border-draw:hover::after {
  width: 100%;
  height: 100%;
  border-bottom-color: var(--color-primary);
  border-left-color: var(--color-primary);
}

/* Pulse glow on hover */
.btn-glow:hover {
  box-shadow: 0 0 0 0 rgba(98, 0, 238, 0.5);
  animation: pulse-glow 1.5s infinite;
}
@keyframes pulse-glow {
  0% { box-shadow: 0 0 0 0 rgba(98, 0, 238, 0.5); }
  70% { box-shadow: 0 0 0 12px rgba(98, 0, 238, 0); }
  100% { box-shadow: 0 0 0 0 rgba(98, 0, 238, 0); }
}
```

### 2d. Custom Cursor Interaction

Subtle cursor follower that enlarges on interactive elements.

```css
.cursor-dot {
  position: fixed;
  top: 0;
  left: 0;
  width: 8px;
  height: 8px;
  background: var(--color-primary);
  border-radius: 50%;
  pointer-events: none;
  z-index: 9999;
  transition: width 0.3s, height 0.3s, margin 0.3s;
  mix-blend-mode: difference;
}

.cursor-dot.is-hovering {
  width: 40px;
  height: 40px;
  margin: -16px 0 0 -16px;
  background: rgba(255, 255, 255, 0.2);
  border: 1px solid #fff;
}
```

```javascript
const cursor = document.querySelector('.cursor-dot');

document.addEventListener('mousemove', (e) => {
  cursor.style.transform = `translate(${e.clientX}px, ${e.clientY}px)`;
});

document.querySelectorAll('a, button, [data-cursor]').forEach((el) => {
  el.addEventListener('mouseenter', () => cursor.classList.add('is-hovering'));
  el.addEventListener('mouseleave', () => cursor.classList.remove('is-hovering'));
});
```

---

## 3. Loading & Entrance Animations

### 3a. Staggered Reveal (CSS Custom Properties)

Uses `--i` (index) custom property to stagger animation delay per item.

```css
.stagger-item {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.5s ease, transform 0.5s ease;
  transition-delay: calc(var(--i, 0) * 80ms);
}

.stagger-item.is-visible {
  opacity: 1;
  transform: translateY(0);
}
```

```html
<div class="stagger-item" style="--i: 0">Item 1</div>
<div class="stagger-item" style="--i: 1">Item 2</div>
<div class="stagger-item" style="--i: 2">Item 3</div>
<div class="stagger-item" style="--i: 3">Item 4</div>
```

```javascript
const staggerObserver = new IntersectionObserver((entries) => {
  entries.forEach((entry) => {
    if (entry.isIntersecting) {
      entry.target.classList.add('is-visible');
      staggerObserver.unobserve(entry.target);
    }
  });
}, { threshold: 0.1 });

document.querySelectorAll('.stagger-item').forEach((el) => {
  staggerObserver.observe(el);
});
```

**Future-proof version with `sibling-index()` (Chrome 133+, no inline styles needed):**
```css
.stagger-item {
  transition-delay: calc((sibling-index() - 1) * 80ms);
  transition: opacity 0.5s ease, transform 0.5s ease;
}
```

### 3b. Skeleton Screen with Shimmer

Pure CSS skeleton loader with a shimmer animation.

```css
/* Skeleton card */
.skeleton {
  width: 100%;
  max-width: 400px;
  border-radius: 12px;
  padding: 20px;
  background: #f0f0f0;
}

.skeleton-line {
  height: 16px;
  margin-bottom: 12px;
  border-radius: 4px;
  background: linear-gradient(
    90deg,
    #e0e0e0 25%,
    #f0f0f0 50%,
    #e0e0e0 75%
  );
  background-size: 200% 100%;
  animation: shimmer 1.5s infinite;
}

.skeleton-line--title {
  width: 60%;
  height: 24px;
}

.skeleton-line--short {
  width: 40%;
}

.skeleton-avatar {
  width: 48px;
  height: 48px;
  border-radius: 50%;
  background: linear-gradient(
    90deg,
    #e0e0e0 25%,
    #f0f0f0 50%,
    #e0e0e0 75%
  );
  background-size: 200% 100%;
  animation: shimmer 1.5s infinite;
}

@keyframes shimmer {
  0% { background-position: 200% 0; }
  100% { background-position: -200% 0; }
}
```

**Self-hiding skeleton using `:empty`:**
```css
.card:empty {
  width: 100%;
  height: 250px;
  background:
    linear-gradient(0.25turn, transparent, #fff, transparent),
    linear-gradient(#eee, #eee),
    radial-gradient(38px circle at 19px 19px, #eee 50%, transparent 51%),
    linear-gradient(#eee, #eee);
  background-repeat: no-repeat;
  background-size: 100% 250px, 100% 180px, 100px 100px, 225px 30px;
  background-position: -100% 0, 0 0, 0 190px, 50px 195px;
  animation: skeleton-load 1.5s infinite;
}

@keyframes skeleton-load {
  to { background-position: 100% 0, 0 0, 0 190px, 50px 195px; }
}
```

### 3c. Page Entrance Animation

Animate the entire page content on first load.

```css
@keyframes page-enter {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

body {
  animation: page-enter 0.6s ease-out;
}

/* Staggered children on page load */
.hero-title {
  animation: page-enter 0.6s ease-out 0.1s both;
}
.hero-subtitle {
  animation: page-enter 0.6s ease-out 0.2s both;
}
.hero-cta {
  animation: page-enter 0.6s ease-out 0.3s both;
}
```

**Using `@starting-style` (Chrome 117+) for entry animations without keyframes:**
```css
.toast,
.modal,
.dropdown {
  opacity: 1;
  transform: translateY(0);
  transition: opacity 0.3s ease, transform 0.3s ease;
}

@starting-style {
  .toast,
  .modal,
  .dropdown {
    opacity: 0;
    transform: translateY(12px);
  }
}
```

### 3d. Progressive Image Loading

Blurred placeholder to full image.

```css
.progressive-img {
  position: relative;
  overflow: hidden;
  background-color: #f0f0f0;
}

.progressive-img img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: filter 0.5s ease, opacity 0.5s ease;
}

.progressive-img img[data-src] {
  filter: blur(20px);
  opacity: 0.6;
}

.progressive-img img.loaded {
  filter: blur(0);
  opacity: 1;
}
```

```javascript
document.querySelectorAll('.progressive-img img[data-src]').forEach((img) => {
  const fullSrc = img.dataset.src;
  const fullImg = new Image();
  fullImg.onload = () => {
    img.src = fullSrc;
    img.classList.add('loaded');
    img.removeAttribute('data-src');
  };
  fullImg.src = fullSrc;
});
```

---

## 4. Modern CSS Effects

### 4a. Backdrop-Filter (Glassmorphism)

Frosted glass effect for headers, cards, modals.

```css
.glass-card {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(12px) saturate(180%);
  -webkit-backdrop-filter: blur(12px) saturate(180%);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 16px;
  padding: 24px;
}

/* Frosted glass navbar */
.glass-nav {
  position: fixed;
  top: 0;
  width: 100%;
  background: rgba(255, 255, 255, 0.7);
  backdrop-filter: blur(10px) saturate(150%);
  -webkit-backdrop-filter: blur(10px) saturate(150%);
  border-bottom: 1px solid rgba(0, 0, 0, 0.05);
  z-index: 100;
}
```

### 4b. Container Queries

Style components based on their container size, not viewport.

```css
.card-wrapper {
  container-type: inline-size;
  container-name: card;
}

/* Default: small card */
.card {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

/* When container is wider than 400px */
@container card (min-width: 400px) {
  .card {
    flex-direction: row;
    align-items: center;
  }
  .card__image {
    width: 40%;
  }
}

/* When container is wider than 700px */
@container card (min-width: 700px) {
  .card {
    gap: 24px;
  }
  .card__title {
    font-size: 1.5rem;
  }
}
```

### 4c. Scroll-State Container Queries (Chrome 133+)

Detect when a sticky element is stuck -- no JS needed.

```css
.header {
  position: sticky;
  top: 0;
  container-type: scroll-state;
}

@container scroll-state((stuck: top)) {
  .header {
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.18);
    backdrop-filter: blur(10px);
  }
}
```

### 4d. Scroll-Snap Carousels

Smooth, touch-friendly horizontal scrolling.

```css
.carousel {
  display: flex;
  gap: 16px;
  overflow-x: auto;
  scroll-snap-type: x mandatory;
  scroll-behavior: smooth;
  -webkit-overflow-scrolling: touch;
  scrollbar-width: none; /* Firefox */
  padding: 20px;
}

.carousel::-webkit-scrollbar {
  display: none;
}

.carousel__item {
  flex: 0 0 min(85vw, 400px);
  scroll-snap-align: center;
  border-radius: 16px;
}
```

### 4e. View Transitions API

Smooth animated transitions when updating DOM or navigating between pages.

**Same-document transition (SPA-style):**
```css
.card {
  view-transition-name: match-element;
}

/* Customize the transition animation */
::view-transition-group(*) {
  animation-duration: 0.4s;
  animation-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
}

::view-transition-old(match-element) {
  animation: fade-out 0.3s ease forwards;
}

::view-transition-new(match-element) {
  animation: fade-in 0.3s ease forwards;
}
```

```javascript
function updateContent(newHTML) {
  if (!document.startViewTransition) {
    // Fallback: just swap content
    document.getElementById('content').innerHTML = newHTML;
    return;
  }

  document.startViewTransition(() => {
    document.getElementById('content').innerHTML = newHTML;
  });
}
```

**Cross-document (MPA) view transitions (Chrome 126+):**
```css
@view-transition {
  navigation: auto;
}

/* Old page fades out, new page fades in */
::view-transition-old(root) {
  animation: fade-out 0.3s ease;
}
::view-transition-new(root) {
  animation: fade-in 0.3s ease;
}
```

### 4f. Modern Color with OKLCH

Perceptually uniform colors with easy manipulation.

```css
:root {
  --brand: oklch(0.62 0.16 35);
  --brand-soft: color-mix(in oklch, var(--brand), white 65%);
  --brand-dark: oklch(from var(--brand) calc(l - 0.15) c h);
}

.button {
  background: var(--brand);
}

.button:hover {
  background: oklch(from var(--brand) calc(l - 0.08) c h);
}
```

### 4g. text-wrap: balance and pretty

```css
h1, h2, h3, .hero-title {
  text-wrap: balance;
}

.prose p {
  text-wrap: pretty;
}
```

---

## 5. Text Effects

### 5a. CSS-Only Typewriter Effect

```css
.typewriter h1 {
  overflow: hidden;
  border-right: 0.15em solid var(--color-primary, orange);
  white-space: nowrap;
  margin: 0 auto;
  letter-spacing: 0.05em;
  animation:
    typing 3.5s steps(40, end),
    blink-caret 0.75s step-end infinite;
}

@keyframes typing {
  from { width: 0; }
  to { width: 100%; }
}

@keyframes blink-caret {
  from, to { border-color: transparent; }
  50% { border-color: var(--color-primary, orange); }
}
```

```html
<div class="typewriter">
  <h1>Building the future of open source.</h1>
</div>
```

**Note:** Adjust `steps()` count to roughly match character count for best effect.

### 5b. JavaScript Typewriter (Multi-String, Flexible)

```javascript
class Typewriter {
  constructor(element, strings, speed = 80, deleteSpeed = 40, pause = 2000) {
    this.element = element;
    this.strings = strings;
    this.speed = speed;
    this.deleteSpeed = deleteSpeed;
    this.pause = pause;
    this.stringIndex = 0;
    this.charIndex = 0;
    this.isDeleting = false;
    this.type();
  }

  type() {
    const current = this.strings[this.stringIndex];

    if (this.isDeleting) {
      this.element.textContent = current.substring(0, this.charIndex - 1);
      this.charIndex--;
    } else {
      this.element.textContent = current.substring(0, this.charIndex + 1);
      this.charIndex++;
    }

    let delay = this.isDeleting ? this.deleteSpeed : this.speed;

    if (!this.isDeleting && this.charIndex === current.length) {
      delay = this.pause;
      this.isDeleting = true;
    } else if (this.isDeleting && this.charIndex === 0) {
      this.isDeleting = false;
      this.stringIndex = (this.stringIndex + 1) % this.strings.length;
      delay = 500;
    }

    setTimeout(() => this.type(), delay);
  }
}

// Usage
new Typewriter(
  document.querySelector('.typewriter-text'),
  ['Build ambitious sites.', 'Scale with confidence.', 'Ship faster.']
);
```

### 5c. Gradient Text with Animation

```css
.gradient-text {
  background: linear-gradient(
    135deg,
    #667eea 0%,
    #764ba2 25%,
    #f093fb 50%,
    #667eea 75%,
    #764ba2 100%
  );
  background-size: 200% auto;
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: gradient-shift 3s ease infinite;
}

@keyframes gradient-shift {
  0% { background-position: 0% center; }
  100% { background-position: 200% center; }
}
```

### 5d. Split Text Character Animation

Wraps each character in a span, then animates with staggered delays.

```javascript
function splitText(element) {
  const text = element.textContent;
  element.textContent = '';
  element.setAttribute('aria-label', text); // Accessibility

  text.split('').forEach((char, i) => {
    const span = document.createElement('span');
    span.textContent = char === ' ' ? '\u00A0' : char;
    span.style.setProperty('--char-index', i);
    span.classList.add('split-char');
    span.setAttribute('aria-hidden', 'true');
    element.appendChild(span);
  });
}

document.querySelectorAll('.split-animate').forEach(splitText);
```

```css
.split-char {
  display: inline-block;
  opacity: 0;
  transform: translateY(20px);
  animation: char-reveal 0.5s ease forwards;
  animation-delay: calc(var(--char-index) * 40ms);
}

@keyframes char-reveal {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Variant: wave effect */
.wave .split-char {
  animation: char-wave 0.6s ease forwards;
  animation-delay: calc(var(--char-index) * 50ms);
}

@keyframes char-wave {
  0% { transform: translateY(40px) rotate(10deg); opacity: 0; }
  60% { transform: translateY(-5px) rotate(-2deg); opacity: 1; }
  100% { transform: translateY(0) rotate(0); opacity: 1; }
}
```

### 5e. Text Scramble/Decode Effect

Letters randomly cycle before resolving to the final text.

```javascript
class TextScramble {
  constructor(element) {
    this.element = element;
    this.chars = '!<>-_\\/[]{}—=+*^?#________';
    this.frame = 0;
    this.queue = [];
    this.resolve = null;
  }

  setText(newText) {
    const oldText = this.element.textContent;
    const length = Math.max(oldText.length, newText.length);
    this.queue = [];

    for (let i = 0; i < length; i++) {
      const from = oldText[i] || '';
      const to = newText[i] || '';
      const start = Math.floor(Math.random() * 40);
      const end = start + Math.floor(Math.random() * 40);
      this.queue.push({ from, to, start, end });
    }

    cancelAnimationFrame(this.frameRequest);
    this.frame = 0;
    this.update();
  }

  update() {
    let output = '';
    let complete = 0;

    for (let i = 0; i < this.queue.length; i++) {
      const { from, to, start, end } = this.queue[i];
      let char;

      if (this.frame >= end) {
        complete++;
        char = to;
      } else if (this.frame >= start) {
        if (Math.random() < 0.28) {
          char = this.chars[Math.floor(Math.random() * this.chars.length)];
        } else {
          char = from;
        }
      } else {
        char = from;
      }
      output += char;
    }

    this.element.textContent = output;

    if (complete < this.queue.length) {
      this.frameRequest = requestAnimationFrame(() => this.update());
      this.frame++;
    }
  }
}

// Usage
const scrambler = new TextScramble(document.querySelector('.scramble-text'));
scrambler.setText('Building the future of open source.');
```

### 5f. Animated Counter

Counts up from 0 to a target number on scroll.

```javascript
function animateCounter(element) {
  const target = parseInt(element.dataset.target, 10);
  const duration = 2000;
  const startTime = performance.now();

  function update(currentTime) {
    const elapsed = currentTime - startTime;
    const progress = Math.min(elapsed / duration, 1);

    // Ease-out cubic
    const eased = 1 - Math.pow(1 - progress, 3);
    const current = Math.round(eased * target);

    element.textContent = current.toLocaleString();

    if (progress < 1) {
      requestAnimationFrame(update);
    }
  }

  requestAnimationFrame(update);
}

// Trigger on scroll into view
const counterObserver = new IntersectionObserver((entries) => {
  entries.forEach((entry) => {
    if (entry.isIntersecting) {
      animateCounter(entry.target);
      counterObserver.unobserve(entry.target);
    }
  });
}, { threshold: 0.5 });

document.querySelectorAll('[data-target]').forEach((el) => {
  counterObserver.observe(el);
});
```

```html
<span class="counter" data-target="14000">0</span>
```

---

## 6. Navigation Patterns

### 6a. Shrinking Header on Scroll

Pure CSS approach with scroll-state queries (Chrome 133+), plus JS fallback.

**Modern CSS-only (Chrome 133+):**
```css
.site-header {
  position: sticky;
  top: 0;
  padding: 24px 32px;
  transition: padding 0.3s ease, box-shadow 0.3s ease, backdrop-filter 0.3s ease;
  container-type: scroll-state;
}

@container scroll-state((stuck: top)) {
  .site-header {
    padding: 12px 32px;
    box-shadow: 0 2px 20px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(12px);
    background: rgba(255, 255, 255, 0.9);
  }

  .site-header .logo {
    height: 32px; /* shrink from e.g. 48px */
  }
}

.site-header .logo {
  height: 48px;
  transition: height 0.3s ease;
}
```

**JavaScript fallback (all browsers):**
```javascript
const header = document.querySelector('.site-header');
let lastScroll = 0;

window.addEventListener('scroll', () => {
  const scrollY = window.scrollY;

  if (scrollY > 50) {
    header.classList.add('is-scrolled');
  } else {
    header.classList.remove('is-scrolled');
  }

  // Optional: hide on scroll down, show on scroll up
  if (scrollY > lastScroll && scrollY > 200) {
    header.classList.add('is-hidden');
  } else {
    header.classList.remove('is-hidden');
  }
  lastScroll = scrollY;
}, { passive: true });
```

```css
.site-header {
  position: sticky;
  top: 0;
  padding: 24px 32px;
  transition: padding 0.3s ease, box-shadow 0.3s ease, transform 0.3s ease;
}

.site-header.is-scrolled {
  padding: 12px 32px;
  box-shadow: 0 2px 20px rgba(0, 0, 0, 0.1);
  backdrop-filter: blur(12px);
  background: rgba(255, 255, 255, 0.9);
}

.site-header.is-hidden {
  transform: translateY(-100%);
}
```

### 6b. Scroll Progress Indicator

```css
.scroll-progress {
  position: fixed;
  top: 0;
  left: 0;
  height: 3px;
  background: var(--color-primary);
  transform-origin: 0 50%;
  transform: scaleX(0);
  z-index: 9999;
  width: 100%;
}

/* CSS-only version (Chrome 115+) */
.scroll-progress {
  animation: grow-progress auto linear;
  animation-timeline: scroll();
}

@keyframes grow-progress {
  from { transform: scaleX(0); }
  to { transform: scaleX(1); }
}
```

**JS fallback:**
```javascript
const progressBar = document.querySelector('.scroll-progress');

window.addEventListener('scroll', () => {
  const scrollTop = document.documentElement.scrollTop;
  const scrollHeight = document.documentElement.scrollHeight - window.innerHeight;
  const progress = scrollTop / scrollHeight;
  progressBar.style.transform = `scaleX(${progress})`;
}, { passive: true });
```

### 6c. Smooth Scroll with Active Section Highlighting

```css
html {
  scroll-behavior: smooth;
}

.nav-link {
  position: relative;
  color: var(--color-text-muted);
  transition: color 0.3s ease;
}

.nav-link.is-active {
  color: var(--color-primary);
}

/* Active indicator underline */
.nav-link::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 0;
  width: 100%;
  height: 2px;
  background: var(--color-primary);
  transform: scaleX(0);
  transition: transform 0.3s ease;
}

.nav-link.is-active::after {
  transform: scaleX(1);
}
```

```javascript
const sections = document.querySelectorAll('section[id]');
const navLinks = document.querySelectorAll('.nav-link');

const sectionObserver = new IntersectionObserver((entries) => {
  entries.forEach((entry) => {
    if (entry.isIntersecting) {
      navLinks.forEach((link) => {
        link.classList.toggle(
          'is-active',
          link.getAttribute('href') === `#${entry.target.id}`
        );
      });
    }
  });
}, {
  threshold: 0.3,
  rootMargin: '-80px 0px -50% 0px' // Account for header height
});

sections.forEach((section) => sectionObserver.observe(section));
```

---

## 7. Hero Section Patterns

### 7a. Animated Gradient Background

```css
.hero {
  min-height: 100vh;
  background: linear-gradient(
    -45deg,
    #ee7752,
    #e73c7e,
    #23a6d5,
    #23d5ab
  );
  background-size: 400% 400%;
  animation: gradient-flow 15s ease infinite;
}

@keyframes gradient-flow {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}
```

**Mesh gradient with blobs:**
```css
.hero-mesh {
  position: relative;
  min-height: 100vh;
  overflow: hidden;
  background: #0a0a0a;
}

.hero-mesh .blob {
  position: absolute;
  border-radius: 50%;
  filter: blur(80px);
  opacity: 0.6;
  animation: blob-float 20s ease-in-out infinite;
}

.hero-mesh .blob:nth-child(1) {
  width: 600px;
  height: 600px;
  background: #7c3aed;
  top: -10%;
  left: -10%;
}

.hero-mesh .blob:nth-child(2) {
  width: 500px;
  height: 500px;
  background: #2563eb;
  top: 50%;
  right: -5%;
  animation-delay: -5s;
  animation-direction: reverse;
}

.hero-mesh .blob:nth-child(3) {
  width: 400px;
  height: 400px;
  background: #06b6d4;
  bottom: -10%;
  left: 30%;
  animation-delay: -10s;
}

@keyframes blob-float {
  0%, 100% { transform: translate(0, 0) scale(1); }
  25% { transform: translate(30px, -50px) scale(1.1); }
  50% { transform: translate(-20px, 20px) scale(0.9); }
  75% { transform: translate(20px, 40px) scale(1.05); }
}
```

### 7b. Morphing Blob Shape

```css
.morph-blob {
  width: 400px;
  height: 400px;
  background: linear-gradient(135deg, #667eea, #764ba2);
  border-radius: 60% 40% 30% 70% / 60% 30% 70% 40%;
  animation: morph 8s ease-in-out infinite;
}

@keyframes morph {
  0% { border-radius: 60% 40% 30% 70% / 60% 30% 70% 40%; }
  25% { border-radius: 30% 60% 70% 40% / 50% 60% 30% 60%; }
  50% { border-radius: 50% 60% 30% 60% / 30% 60% 70% 40%; }
  75% { border-radius: 40% 60% 50% 70% / 60% 40% 60% 30%; }
  100% { border-radius: 60% 40% 30% 70% / 60% 30% 70% 40%; }
}
```

### 7c. Canvas Particle Effect

Lightweight particle system for hero backgrounds.

```javascript
class ParticleHero {
  constructor(canvas) {
    this.canvas = canvas;
    this.ctx = canvas.getContext('2d');
    this.particles = [];
    this.mouse = { x: null, y: null };
    this.resize();

    window.addEventListener('resize', () => this.resize());
    canvas.addEventListener('mousemove', (e) => {
      this.mouse.x = e.offsetX;
      this.mouse.y = e.offsetY;
    });
    canvas.addEventListener('mouseleave', () => {
      this.mouse.x = null;
      this.mouse.y = null;
    });

    this.init();
    this.animate();
  }

  resize() {
    this.canvas.width = this.canvas.offsetWidth;
    this.canvas.height = this.canvas.offsetHeight;
  }

  init() {
    this.particles = [];
    const count = Math.floor((this.canvas.width * this.canvas.height) / 8000);

    for (let i = 0; i < count; i++) {
      this.particles.push({
        x: Math.random() * this.canvas.width,
        y: Math.random() * this.canvas.height,
        vx: (Math.random() - 0.5) * 0.5,
        vy: (Math.random() - 0.5) * 0.5,
        radius: Math.random() * 2 + 0.5,
      });
    }
  }

  animate() {
    this.ctx.clearRect(0, 0, this.canvas.width, this.canvas.height);

    this.particles.forEach((p) => {
      p.x += p.vx;
      p.y += p.vy;

      // Wrap around edges
      if (p.x < 0) p.x = this.canvas.width;
      if (p.x > this.canvas.width) p.x = 0;
      if (p.y < 0) p.y = this.canvas.height;
      if (p.y > this.canvas.height) p.y = 0;

      // Draw particle
      this.ctx.beginPath();
      this.ctx.arc(p.x, p.y, p.radius, 0, Math.PI * 2);
      this.ctx.fillStyle = 'rgba(255, 255, 255, 0.6)';
      this.ctx.fill();
    });

    // Draw connections
    for (let i = 0; i < this.particles.length; i++) {
      for (let j = i + 1; j < this.particles.length; j++) {
        const dx = this.particles[i].x - this.particles[j].x;
        const dy = this.particles[i].y - this.particles[j].y;
        const dist = Math.sqrt(dx * dx + dy * dy);

        if (dist < 120) {
          this.ctx.beginPath();
          this.ctx.moveTo(this.particles[i].x, this.particles[i].y);
          this.ctx.lineTo(this.particles[j].x, this.particles[j].y);
          this.ctx.strokeStyle = `rgba(255, 255, 255, ${0.15 * (1 - dist / 120)})`;
          this.ctx.lineWidth = 0.5;
          this.ctx.stroke();
        }
      }
    }

    // Mouse interaction: repel nearby particles
    if (this.mouse.x !== null) {
      this.particles.forEach((p) => {
        const dx = p.x - this.mouse.x;
        const dy = p.y - this.mouse.y;
        const dist = Math.sqrt(dx * dx + dy * dy);
        if (dist < 100) {
          p.x += dx * 0.02;
          p.y += dy * 0.02;
        }
      });
    }

    requestAnimationFrame(() => this.animate());
  }
}

// Usage
const canvas = document.querySelector('#particle-canvas');
if (canvas) new ParticleHero(canvas);
```

```html
<section class="hero" style="position: relative;">
  <canvas id="particle-canvas"
    style="position: absolute; inset: 0; width: 100%; height: 100%;"></canvas>
  <div class="hero-content" style="position: relative; z-index: 1;">
    <!-- content -->
  </div>
</section>
```

### 7d. Noise/Grain Texture Overlay

Adds a subtle film grain to hero sections for a premium feel.

```css
.hero::after {
  content: '';
  position: absolute;
  inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.65' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)'/%3E%3C/svg%3E");
  opacity: 0.04;
  pointer-events: none;
  z-index: 1;
}
```

---

## 8. Card & Grid Interactions

### 8a. 3D Card Tilt on Hover

Tracks mouse position over the card to apply perspective-based rotation.

```css
.tilt-card {
  border-radius: 16px;
  padding: 32px;
  background: #fff;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
  transition: transform 0.1s ease, box-shadow 0.3s ease;
  transform-style: preserve-3d;
  will-change: transform;
}

.tilt-card:hover {
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15);
}

/* Inner content gets a slight Z push for depth */
.tilt-card__inner {
  transform: translateZ(30px);
  transition: transform 0.3s ease;
}
```

```javascript
document.querySelectorAll('.tilt-card').forEach((card) => {
  card.addEventListener('mousemove', (e) => {
    const rect = card.getBoundingClientRect();
    const x = e.clientX - rect.left; // x within card
    const y = e.clientY - rect.top;  // y within card
    const centerX = rect.width / 2;
    const centerY = rect.height / 2;

    const rotateX = ((y - centerY) / centerY) * -8; // max 8deg
    const rotateY = ((x - centerX) / centerX) * 8;

    card.style.transform = `perspective(600px) rotateX(${rotateX}deg) rotateY(${rotateY}deg)`;
  });

  card.addEventListener('mouseleave', () => {
    card.style.transform = 'perspective(600px) rotateX(0) rotateY(0)';
    card.style.transition = 'transform 0.5s ease';
  });

  card.addEventListener('mouseenter', () => {
    card.style.transition = 'transform 0.1s ease';
  });
});
```

### 8b. CSS-Only Card Hover Effects

```css
/* Lift + shadow */
.card {
  border-radius: 16px;
  overflow: hidden;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card:hover {
  transform: translateY(-8px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.12);
}

/* Image zoom on card hover */
.card__image {
  overflow: hidden;
}

.card__image img {
  transition: transform 0.5s cubic-bezier(0.4, 0, 0.2, 1);
}

.card:hover .card__image img {
  transform: scale(1.08);
}

/* Border gradient on hover */
.card-border-glow {
  position: relative;
  border-radius: 16px;
  padding: 1px;
  background: linear-gradient(135deg, transparent 40%, var(--color-primary) 100%);
  opacity: 0;
  transition: opacity 0.3s ease;
}

.card-border-glow:hover {
  opacity: 1;
}

/* Overlay reveal on hover */
.card-overlay {
  position: relative;
  overflow: hidden;
}

.card-overlay::after {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, rgba(0, 0, 0, 0.7) 0%, transparent 60%);
  opacity: 0;
  transition: opacity 0.3s ease;
}

.card-overlay:hover::after {
  opacity: 1;
}
```

### 8c. Staggered Grid Reveal

Grid items animate in with staggered delays when scrolled into view.

```css
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 24px;
}

.grid__item {
  opacity: 0;
  transform: translateY(30px) scale(0.97);
  transition: opacity 0.5s ease, transform 0.5s ease;
  transition-delay: calc(var(--i, 0) * 100ms);
}

.grid__item.is-visible {
  opacity: 1;
  transform: translateY(0) scale(1);
}
```

```javascript
const gridItems = document.querySelectorAll('.grid__item');

// Assign stagger index
gridItems.forEach((item, i) => {
  item.style.setProperty('--i', i % 6); // Reset stagger every 6 items
});

const gridObserver = new IntersectionObserver((entries) => {
  entries.forEach((entry) => {
    if (entry.isIntersecting) {
      entry.target.classList.add('is-visible');
      gridObserver.unobserve(entry.target);
    }
  });
}, { threshold: 0.05 });

gridItems.forEach((item) => gridObserver.observe(item));
```

### 8d. Masonry Layout (CSS Grid Lanes -- Emerging)

```css
/* Future standard: grid-lanes (Chrome Canary behind flag) */
.masonry-grid {
  display: grid-lanes;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
}

/* Current workaround: columns */
.masonry-fallback {
  columns: 3;
  column-gap: 16px;
}

.masonry-fallback > * {
  break-inside: avoid;
  margin-bottom: 16px;
}
```

---

## 9. Performance

### 9a. Animation Performance Tier List

**Tier S (Compositor-only, best performance):**
- `transform` (translate, rotate, scale)
- `opacity`
- `filter`
- `clip-path`

These properties are composited on the GPU and do not trigger layout or paint.

**Tier A (Paint only, no layout):**
- `background-color`
- `color`
- `box-shadow`
- `border-color`

**Tier F (Triggers layout -- AVOID animating):**
- `width`, `height`
- `top`, `left`, `right`, `bottom`
- `margin`, `padding`
- `font-size`
- `border-width`

### 9b. GPU Acceleration

```css
/* Promote to compositor layer for smooth animation */
.animated-element {
  will-change: transform;
  /* Or use the classic hack: */
  /* transform: translateZ(0); */
}

/* IMPORTANT: Don't overuse will-change. Apply only to elements
   that are actively animating. Too many layers = memory bloat. */

/* Best practice: add will-change right before animation starts */
.card:hover {
  will-change: transform;
  transform: translateY(-8px);
}
```

```javascript
// Programmatic will-change management
element.addEventListener('mouseenter', () => {
  element.style.willChange = 'transform';
});

element.addEventListener('transitionend', () => {
  element.style.willChange = 'auto';
});
```

### 9c. prefers-reduced-motion

Always respect user motion preferences. This is an accessibility requirement.

```css
/* Remove all animations for users who prefer reduced motion */
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}

/* Or selectively: keep essential transitions, remove decorative ones */
@media (prefers-reduced-motion: reduce) {
  .parallax-layer,
  .morph-blob,
  .gradient-text,
  .particle-canvas {
    animation: none;
  }

  .reveal {
    opacity: 1;
    transform: none;
    transition: none;
  }

  .hero {
    background-size: cover; /* Stop gradient animation */
    animation: none;
  }
}
```

```javascript
// Check in JS before starting animations
const prefersReducedMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;

if (!prefersReducedMotion) {
  // Start particle effects, scroll animations, etc.
  new ParticleHero(canvas);
}
```

### 9d. Lazy Loading

```html
<!-- Native lazy loading for images -->
<img src="placeholder.jpg"
     data-src="full-image.jpg"
     loading="lazy"
     decoding="async"
     alt="Description">

<!-- Native lazy loading for iframes -->
<iframe src="embed.html" loading="lazy"></iframe>
```

```javascript
// IntersectionObserver-based lazy loading for more control
const lazyImages = document.querySelectorAll('img[data-src]');

const imageObserver = new IntersectionObserver((entries) => {
  entries.forEach((entry) => {
    if (entry.isIntersecting) {
      const img = entry.target;
      img.src = img.dataset.src;
      if (img.dataset.srcset) img.srcset = img.dataset.srcset;
      img.removeAttribute('data-src');
      imageObserver.unobserve(img);
    }
  });
}, {
  rootMargin: '200px 0px' // Start loading 200px before visible
});

lazyImages.forEach((img) => imageObserver.observe(img));
```

### 9e. Scroll Event Optimization

```javascript
// ALWAYS use passive listeners for scroll events
window.addEventListener('scroll', onScroll, { passive: true });

// Throttle with requestAnimationFrame
let ticking = false;

function onScroll() {
  if (!ticking) {
    requestAnimationFrame(() => {
      // Do your scroll-based work here
      updateScrollEffects();
      ticking = false;
    });
    ticking = true;
  }
}
```

### 9f. Content-Visibility for Off-Screen Content

Skip rendering of off-screen sections entirely.

```css
section {
  content-visibility: auto;
  contain-intrinsic-size: auto 500px; /* Estimated height */
}
```

### 9g. Font Loading Optimization

```css
/* Prevent layout shift from font loading */
@font-face {
  font-family: 'CustomFont';
  src: url('font.woff2') format('woff2');
  font-display: swap;
  /* optional: use 'optional' for non-critical fonts */
}
```

---

## Browser Support Quick Reference

| Feature | Chrome | Firefox | Safari | Edge |
|---|---|---|---|---|
| IntersectionObserver | 51+ | 55+ | 12.1+ | 15+ |
| scroll-driven animations (`animation-timeline`) | 115+ | Behind flag | Not yet | 115+ |
| `@container` (size queries) | 105+ | 110+ | 16+ | 105+ |
| `@container scroll-state()` | 133+ | Not yet | Not yet | 133+ |
| `backdrop-filter` | 76+ | 103+ | 9+ | 79+ |
| View Transitions (same-doc) | 111+ | Not yet | 18+ | 111+ |
| View Transitions (cross-doc) | 126+ | Not yet | Not yet | 126+ |
| `scroll-snap` | 69+ | 68+ | 11+ | 79+ |
| `@starting-style` | 117+ | Not yet | 17.5+ | 117+ |
| `content-visibility` | 85+ | 124+ | Not yet | 85+ |
| `text-wrap: balance` | 114+ | 121+ | Not yet | 114+ |
| `sibling-index()` | 133+ | Not yet | Not yet | 133+ |
| OKLCH colors | 111+ | 113+ | 15.4+ | 111+ |

---

## Sources

- [Bringing Back Parallax With Scroll-Driven CSS Animations -- CSS-Tricks](https://css-tricks.com/bringing-back-parallax-with-scroll-driven-css-animations/)
- [Animate elements on scroll with Scroll-driven animations -- Chrome Developers](https://developer.chrome.com/docs/css-ui/scroll-driven-animations)
- [Scroll-Driven Animations Style](https://scroll-driven-animations.style/)
- [Magnetic Hover Effect with Vanilla JavaScript -- Init HTML](https://en.inithtml.com/resources/magnetic-hover-effect-creating-cursor-attracted-buttons-with-vanilla-javascript/)
- [How to Recreate the Ripple Effect of Material Design Buttons -- CSS-Tricks](https://css-tricks.com/how-to-recreate-the-ripple-effect-of-material-design-buttons/)
- [10 Simple CSS and JavaScript Micro-interactions for Buttons -- SitePoint](https://www.sitepoint.com/button-micro-interactions/)
- [2026 CSS Features You Must Know -- Riad Kilani](https://blog.riadkilani.com/2026-css-features-you-must-know/)
- [What's new in view transitions (2025 update) -- Chrome Developers](https://developer.chrome.com/blog/view-transitions-in-2025)
- [6 CSS Snippets Every Front-End Developer Should Know In 2025](https://nerdy.dev/6-css-snippets-every-front-end-developer-should-know-in-2025)
- [CSS Scroll-Driven Animations for Section-Based Scroll Progress Indicators -- Frontend Masters](https://frontendmasters.com/blog/using-css-scroll-driven-animations-for-section-based-scroll-progress-indicators/)
- [CSS Typewriter Effect -- CSS-Tricks](https://css-tricks.com/snippets/css/typewriter-effect/)
- [CSS Skeleton Loading Screen Animation -- DEV Community](https://dev.to/michaelburrows/css-skeleton-loading-screen-animation-gj3)
- [CSS GPU Acceleration: will-change & translate3d Guide -- Lexo](https://www.lexo.ch/blog/2025/01/boost-css-performance-with-will-change-and-transform-translate3d-why-gpu-acceleration-matters/)
- [Design accessible animation and movement -- Pope Tech](https://blog.pope.tech/2025/12/08/design-accessible-animation-and-movement/)
- [CSS Animation Performance -- Useful Functions](https://www.usefulfunctions.co.uk/2025/11/08/css-animation-performance-gpu-acceleration-techniques/)
- [3D Tilt Effect on Hover Using Vanilla JS -- CodeHim](https://codehim.com/animation-effects/3d-tilt-effect-on-hover-using-vanilla-js/)
- [backdrop-filter -- MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/backdrop-filter)
- [prefers-reduced-motion -- CSS-Tricks](https://css-tricks.com/almanac/rules/m/media/prefers-reduced-motion/)
- [CSS scroll-state() -- Chrome Developers](https://developer.chrome.com/blog/css-scroll-state-queries)
- [Web Animation Performance Tier List -- Motion Magazine](https://motion.dev/magazine/web-animation-performance-tier-list)

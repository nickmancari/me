<script setup>
import { onMounted, onUnmounted, ref } from 'vue'

const scrolled = ref(false)

function onScroll() {
  scrolled.value = window.scrollY > 8
}

onMounted(() => {
  onScroll()
  window.addEventListener('scroll', onScroll, { passive: true })
})

onUnmounted(() => {
  window.removeEventListener('scroll', onScroll)
})
</script>

<template>
  <a href="#main" class="skip-link">Skip to content</a>
  <nav class="site-nav" :class="{ 'is-scrolled': scrolled }">
    <div class="nav-inner">
      <RouterLink to="/" class="nav-home">Nick Mancari</RouterLink>
      <div class="nav-links">
        <RouterLink to="/resume" class="nav-link">Resume</RouterLink>
        <RouterLink to="/blog"  class="nav-link">Blog</RouterLink>
        <RouterLink to="/about" class="nav-link">About</RouterLink>
      </div>
    </div>
  </nav>
  <RouterView />
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,300;0,9..144,400;0,9..144,600;1,9..144,300;1,9..144,400;1,9..144,600&family=Lora:ital,wght@0,400;0,500;1,400;1,500&display=swap');

:root {
  --paper:  #ede5d2;
  --ink:    #1e1c17;
  --muted:  #6b6558;
  --accent: #b8472a;
  --rule:   #d4cbb7;
  --maxw:   680px;
  --gutter: 1.5rem;
}

* { margin: 0; padding: 0; box-sizing: border-box; }

html {
  scroll-behavior: smooth;
  scroll-padding-top: 5rem;
}

body {
  background-color: var(--paper);
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='300' height='300'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.65' numOctaves='4' stitchTiles='stitch'/%3E%3CfeColorMatrix type='saturate' values='0'/%3E%3C/filter%3E%3Crect width='300' height='300' filter='url(%23n)' opacity='0.095'/%3E%3C/svg%3E");
  background-size: 280px 280px;
  color: var(--ink);
  font-family: 'Lora', Georgia, serif;
  -webkit-font-smoothing: antialiased;
  line-height: 1.65;
}

body::after {
  content: '';
  position: fixed;
  inset: 0;
  background: radial-gradient(ellipse at 50% 35%, transparent 50%, rgba(18, 12, 4, 0.18) 100%);
  pointer-events: none;
  z-index: 9999;
}

.page {
  max-width: var(--maxw);
  margin: 0 auto;
  padding: clamp(2.5rem, 6vw, 5rem) var(--gutter) 4rem;
}

/* Accessible focus ring for keyboard users */
a:focus-visible {
  outline: 2px solid var(--accent);
  outline-offset: 3px;
  border-radius: 2px;
}

/* Skip link — visible only when focused */
.skip-link {
  position: absolute;
  left: var(--gutter);
  top: -3rem;
  z-index: 100;
  background: var(--paper);
  color: var(--ink);
  font-family: 'Lora', serif;
  font-size: 0.85rem;
  padding: 0.5rem 0.9rem;
  border: 1px solid var(--rule);
  border-radius: 4px;
  text-decoration: none;
  transition: top 0.2s ease;
}
.skip-link:focus { top: 0.6rem; }

/* ── Navbar ─────────────────────────────────────────────────────── */
.site-nav {
  position: sticky;
  top: 0;
  z-index: 50;
  border-bottom: 1px solid transparent;
  background: rgba(237, 229, 210, 0.72);
  backdrop-filter: saturate(140%) blur(10px);
  -webkit-backdrop-filter: saturate(140%) blur(10px);
  transition: border-color 0.25s ease, box-shadow 0.25s ease, background 0.25s ease;
}
.site-nav.is-scrolled {
  border-bottom-color: var(--rule);
  background: rgba(237, 229, 210, 0.86);
  box-shadow: 0 1px 12px rgba(30, 24, 10, 0.06);
}
.nav-inner {
  max-width: var(--maxw);
  margin: 0 auto;
  padding: 1.05rem var(--gutter);
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  gap: 1rem;
}
.nav-home {
  font-family: 'Fraunces', serif;
  font-weight: 600;
  font-variation-settings: 'opsz' 72;
  font-size: 1.05rem;
  text-decoration: none;
  color: var(--ink);
  letter-spacing: -0.01em;
  white-space: nowrap;
  transition: color 0.18s;
}
.nav-home:hover { color: var(--accent); }
.nav-links {
  display: flex;
  gap: clamp(1.1rem, 4vw, 1.8rem);
}
.nav-link {
  position: relative;
  font-family: 'Lora', serif;
  font-size: 0.88rem;
  color: var(--muted);
  text-decoration: none;
  letter-spacing: 0.02em;
  padding-bottom: 2px;
  transition: color 0.18s;
}
/* Animated underline indicator */
.nav-link::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: -1px;
  width: 100%;
  height: 1px;
  background: var(--accent);
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.22s ease;
}
.nav-link:hover { color: var(--accent); }
.nav-link:hover::after { transform: scaleX(1); }
.nav-link.router-link-active {
  color: var(--accent);
}
.nav-link.router-link-active::after { transform: scaleX(1); }

@media (prefers-reduced-motion: reduce) {
  html { scroll-behavior: auto; }
  .nav-link::after { transition: none; }
}
</style>
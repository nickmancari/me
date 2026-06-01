<template>
  <nav class="site-nav">
    <div class="nav-inner">
      <RouterLink to="/" class="nav-home">Nick Mancari</RouterLink>
      <div class="nav-links">
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
}

* { margin: 0; padding: 0; box-sizing: border-box; }

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
  max-width: 680px;
  margin: 0 auto;
  padding: clamp(2.5rem, 6vw, 5rem) 1.5rem 4rem;
}

/* ── Navbar ─────────────────────────────────────────────────────── */
.site-nav {
  border-bottom: 1px solid var(--rule);
}
.nav-inner {
  max-width: 680px;
  margin: 0 auto;
  padding: 1.1rem 1.5rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.nav-home {
  font-family: 'Fraunces', serif;
  font-weight: 600;
  font-variation-settings: 'opsz' 72;
  font-size: 1.05rem;
  text-decoration: none;
  color: var(--ink);
  letter-spacing: -0.01em;
  transition: color 0.18s;
}
.nav-home:hover { color: var(--accent); }
.nav-links {
  display: flex;
  gap: 1.8rem;
}
.nav-link {
  font-family: 'Lora', serif;
  font-size: 0.88rem;
  color: var(--muted);
  text-decoration: none;
  letter-spacing: 0.02em;
  transition: color 0.18s;
}
.nav-link:hover,
.nav-link.router-link-active { color: var(--accent); }
</style>

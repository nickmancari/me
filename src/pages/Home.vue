<script setup>
import portrait from '../assets/portrait.jpg'

const profile = {
  name: 'Nick Mancari',
  role: 'Software Engineer',
  location: 'Roaring Springs, Texas (rural Texas Panhandle)',
  bio: `Software engineer with 4+ years building and shipping full-stack production systems in Ruby on Rails, Go, Vue.js, and MongoDB, including LLM-powered features from integration through production rollout. ` +
  `Backed by a decade in technical support and systems, giving me unusually deep product, debugging, and customer insight. ` +
  `I own features end-to-end — architecture, test coverage, deployment, and the messy production realities most engineers only see secondhand.`,
  body: `Working currently in Healthcare Information Analytics, bringing AI tools to production for the top 300 healthcare providers.`,
  tail: `Founding maintainer of the open-source HL7 developer test tools at hl7x.com.`,
  links: [
    { label: 'Email',    url: 'mailto:nickjmancari@gmail.com' },
    { label: 'GitHub',   url: 'https://github.com/nickmancari' },
    { label: 'LinkedIn', url: 'https://www.linkedin.com/in/nick-mancari-374484200/' },
    { label: 'hl7x',     url: 'https://hl7x.com' },
  ],
}

const projects = [
  {
    title: 'HL7x',
    year: 2026,
    blurb: 'Site for HL7 developer testing tools — elevating the HL7 developer experience.',
    tags: ['Vue', 'GitHub'],
    url: 'https://hl7x.com',
  },
  {
    title: 'kodimcp',
    year: 2025,
    blurb: 'Simple, pluggable local MCP server for the Kodi entertainment system.',
    tags: ['Go', 'API', 'MCP', 'Ollama'],
    url: 'https://github.com/nickmancari/kodimcp',
  },
  {
    title: 'placebo',
    year: 2023,
    blurb: 'Powerful, lightweight open-source HL7 CLI testing tool.',
    tags: ['Go', 'Docker'],
    url: '',
  },
]

const isExternal = (url) => /^https?:\/\//.test(url)
const hasLink = (url) => !!url && url !== '#'
</script>

<template>
  <main id="main" class="page">
    <!-- ── Header / bio ─────────────────────────────────────────── -->
    <header class="intro">
      <div class="intro-top">
        <img
          class="portrait"
          :src="portrait"
          width="900"
          height="1200"
          alt="Portrait of Nick Mancari"
          fetchpriority="high"
        />
        <div class="intro-head">
          <p class="eyebrow">{{ profile.location }}</p>
          <h1 class="name">{{ profile.name }}</h1>
          <p class="role">{{ profile.role }}</p>
        </div>
      </div>

      <div class="bio-block">
        <p class="bio">{{ profile.bio }}</p>
        <p class="body">{{ profile.body }}</p>
        <p class="tail">{{ profile.tail }}</p>
      </div>

      <nav class="links" aria-label="Contact and profiles">
        <a
          v-for="link in profile.links"
          :key="link.label"
          :href="link.url"
          class="link"
          :target="isExternal(link.url) ? '_blank' : null"
          :rel="isExternal(link.url) ? 'noopener noreferrer' : null"
        >{{ link.label }}<span v-if="isExternal(link.url)" class="link-ext" aria-hidden="true">↗</span></a>
      </nav>
    </header>

    <!-- ── Ornament ──────────────────────────────────────────────── -->
    <div class="ornament" aria-hidden="true">❧</div>

    <!-- ── Portfolio ────────────────────────────────────────────── -->
    <section class="work" aria-labelledby="work-label">
      <h2 id="work-label" class="section-label">Selected Work</h2>
      <ul class="projects">
        <li
          v-for="(project, i) in projects"
          :key="project.title"
          class="project"
          :style="{ animationDelay: `${0.08 * i}s` }"
        >
          <component
            :is="hasLink(project.url) ? 'a' : 'div'"
            :href="hasLink(project.url) ? project.url : null"
            :target="isExternal(project.url) ? '_blank' : null"
            :rel="isExternal(project.url) ? 'noopener noreferrer' : null"
            class="project-link"
            :class="{ 'is-static': !hasLink(project.url) }"
          >
            <span class="project-year">{{ project.year }}</span>
            <span class="project-body">
              <span class="project-title">
                {{ project.title }}<span
                  v-if="isExternal(project.url)"
                  class="project-arrow"
                  aria-hidden="true"
                >↗</span>
              </span>
              <span class="project-blurb">{{ project.blurb }}</span>
              <span class="project-tags">
                <span v-for="tag in project.tags" :key="tag" class="tag">{{ tag }}</span>
              </span>
            </span>
          </component>
        </li>
      </ul>
    </section>

    <footer class="footer">
      <p>© {{ new Date().getFullYear() }} {{ profile.name }}</p>
    </footer>
  </main>
</template>

<style>
/* ── Intro ──────────────────────────────────────────────────────── */
.intro-top {
  display: flex;
  align-items: center;
  gap: clamp(1.4rem, 4vw, 2.2rem);
}
.intro-head { min-width: 0; }

/* ── Portrait ───────────────────────────────────────────────────── */
.portrait {
  flex: none;
  width: clamp(7.5rem, 26vw, 11rem);
  aspect-ratio: 3 / 4;
  height: auto;
  object-fit: cover;
  object-position: 50% 30%;
  border-radius: 4px;
  border: 1px solid var(--rule);
  /* Layered shadow + faint warm rim to seat it on the paper */
  box-shadow:
    0 1px 0 rgba(255, 255, 255, 0.4) inset,
    0 2px 4px rgba(30, 24, 10, 0.10),
    0 10px 28px rgba(30, 24, 10, 0.16);
  /* Subtle warmth so the photo harmonizes with the palette */
  filter: saturate(0.92) contrast(1.02);
}

.bio-block,
.links { max-width: 38rem; }

.eyebrow {
  font-family: 'Lora', serif;
  font-style: italic;
  font-size: 0.9rem;
  letter-spacing: 0.01em;
  color: var(--muted);
  margin-bottom: 1.4rem;
}
.name {
  font-family: 'Fraunces', serif;
  font-weight: 600;
  font-variation-settings: 'opsz' 144;
  font-size: clamp(2.6rem, 8vw, 4rem);
  line-height: 1.02;
  letter-spacing: -0.015em;
  text-shadow:
    1px 1px 0   rgba(30, 24, 10, 0.12),
    2px 3px 8px rgba(30, 24, 10, 0.10),
    0   0  24px rgba(184, 71, 42, 0.06);
}
.role {
  font-family: 'Fraunces', serif;
  font-style: italic;
  font-variation-settings: 'opsz' 36;
  color: var(--accent);
  font-size: 1.2rem;
  margin-top: 0.6rem;
  letter-spacing: 0.01em;
}

/* ── Bio paragraphs (proper vertical rhythm, no <br>) ───────────── */
.bio-block { margin-top: 1.9rem; }
.bio,
.body,
.tail {
  color: #3a382f;
  line-height: 1.78;
  font-size: 0.98rem;
}
.body { margin-top: 1.15rem; }
.tail {
  margin-top: 1.15rem;
  font-style: italic;
  color: #4a473e;
}
.bio::first-letter {
  font-family: 'Fraunces', serif;
  font-weight: 600;
  font-variation-settings: 'opsz' 144;
  font-size: 4em;
  line-height: 0.78;
  float: left;
  margin-right: 0.06em;
  padding-top: 0.04em;
  color: var(--accent);
}

/* ── Links ──────────────────────────────────────────────────────── */
.links {
  margin-top: 2.2rem;
  display: flex;
  flex-wrap: wrap;
  gap: 1.6rem;
}
.link {
  color: var(--ink);
  text-decoration: underline;
  text-decoration-thickness: 1px;
  text-underline-offset: 3px;
  text-decoration-color: var(--rule);
  font-size: 0.9rem;
  transition: color 0.18s, text-decoration-color 0.18s;
}
.link:hover { color: var(--accent); text-decoration-color: var(--accent); }
.link-ext {
  font-size: 0.72em;
  margin-left: 0.18em;
  vertical-align: 0.12em;
  text-decoration: none;
  display: inline-block;
}

/* ── Ornament ───────────────────────────────────────────────────── */
.ornament {
  text-align: center;
  color: var(--accent);
  opacity: 0.55;
  font-family: 'Fraunces', serif;
  font-size: 2rem;
  letter-spacing: 0;
  margin: clamp(3rem, 8vw, 5.5rem) 0 clamp(2.5rem, 7vw, 4rem);
  user-select: none;
}

/* ── Work ───────────────────────────────────────────────────────── */
.section-label {
  display: flex;
  align-items: center;
  gap: 1rem;
  font-size: 0.73rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--muted);
  font-weight: 500;
  padding-bottom: 1rem;
  border-bottom: 1px solid var(--rule);
}
.section-label::before,
.section-label::after {
  content: '';
  flex: 1;
  height: 1px;
  background: var(--rule);
}
.projects { list-style: none; }

.project {
  opacity: 0;
  animation: rise 0.5s ease forwards;
}
@keyframes rise {
  from { opacity: 0; transform: translateY(10px); }
  to   { opacity: 1; transform: translateY(0); }
}

.project-link {
  display: grid;
  grid-template-columns: 4rem 1fr;
  gap: 1.2rem;
  text-decoration: none;
  color: inherit;
  padding: 1.6rem 0.6rem;
  border-bottom: 1px solid var(--rule);
  transition: background 0.2s ease, padding-left 0.2s ease;
  margin: 0 -0.6rem;
  border-radius: 3px;
}
a.project-link:hover {
  background: rgba(184, 71, 42, 0.04);
  padding-left: 1rem;
}
.project-link.is-static { cursor: default; }

.project-year {
  font-size: 0.83rem;
  color: var(--muted);
  padding-top: 0.4rem;
  font-variant-numeric: oldstyle-nums;
}
.project-body { display: flex; flex-direction: column; gap: 0.45rem; }
.project-title {
  font-family: 'Fraunces', serif;
  font-variation-settings: 'opsz' 48;
  font-size: 1.45rem;
  transition: color 0.18s;
}
a.project-link:hover .project-title { color: var(--accent); }
.project-arrow {
  font-size: 0.6em;
  margin-left: 0.3em;
  vertical-align: 0.22em;
  color: var(--accent);
  opacity: 0;
  transform: translate(-2px, 2px);
  display: inline-block;
  transition: opacity 0.2s ease, transform 0.2s ease;
}
a.project-link:hover .project-arrow { opacity: 0.85; transform: translate(0, 0); }
.project-blurb { font-family: 'Lora', serif; color: #4a473e; font-size: 0.93rem; line-height: 1.6; }
.project-tags { display: flex; flex-wrap: wrap; gap: 0.45rem; margin-top: 0.25rem; }
.tag {
  font-size: 0.68rem;
  letter-spacing: 0.09em;
  text-transform: uppercase;
  color: var(--accent);
  border: 1px solid rgba(184, 71, 42, 0.28);
  border-radius: 3px;
  padding: 0.18rem 0.55rem;
  background: rgba(184, 71, 42, 0.06);
}

/* ── Footer ─────────────────────────────────────────────────────── */
.footer {
  margin-top: 4.5rem;
  font-size: 0.8rem;
  color: var(--muted);
  text-align: center;
}
.footer::before {
  content: '· · ·';
  display: block;
  letter-spacing: 0.6em;
  color: var(--rule);
  margin-bottom: 1.4rem;
  font-size: 0.9rem;
}

@media (prefers-reduced-motion: reduce) {
  .project { animation: none; opacity: 1; }
}

@media (max-width: 560px) {
  .intro-top {
    flex-direction: column;
    align-items: flex-start;
    gap: 1.3rem;
  }
  .portrait { width: clamp(8.5rem, 42vw, 11rem); }
}

@media (max-width: 480px) {
  .project-link { grid-template-columns: 1fr; gap: 0.5rem; }
  .project-year { padding-top: 0; }
  .bio::first-letter { float: none; font-size: 1em; color: inherit; padding-top: 0; }
}
</style>
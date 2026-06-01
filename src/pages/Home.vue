<script setup>
const profile = {
  name: 'Nick Mancari',
  role: 'Software Engineer',
  location: 'Roaring Springs, Texas (rural Texas Panhandle)',
  bio: `Software engineer with 4+ years building and shipping full-stack production systems in Ruby on Rails, Go, Vue.js, and MongoDB, including LLM-powered features from integration through production rollout. ` +
  `Backed by a decade in technical support and systems, giving me unusually deep product, debugging, and customer insight. ` +
  `I own features end-to-end — architecture, test coverage, deployment, and the messy production realities most engineers only see secondhand`,
  tail: `The founding maintainer of the open source developer HL7 test tools at hl7x.com`,
  links: [
    { label: 'Email',    url: 'mailto:nickjmancari@gmail.com' },
    { label: 'GitHub',   url: 'https://github.com/nickmancari' },
    { label: 'LinkedIn', url: 'https://www.linkedin.com/in/nick-mancari-374484200/' },
    { label: 'hl7x', url: 'https://hl7x.com' },
  ],
}

const projects = [
  {
    title: 'HL7x',
    year: 2024,
    blurb: 'Site for HL7 developer testing tools -- the HL7 developer experience.',
    tags: ['Vue', 'Github'],
    url: 'https:hl7x.com'
  },
  {
    title: 'kodimcp',
    year: '2025',
    blurb: 'Simple, pluggable local MCP server for Kodi entertainment system.',
    tags: ['Go', 'API', 'MCP', 'Ollama'],
    url: 'https://github.com/nickmancari/kodimcp',
  },
  {
    title: 'placebo',
    year: '2023',
    blurb: 'Powerful open source lightweight HL7 CLI testing tool.',
    tags: ['Go', 'Docker'],
    url: '#',
  },
]
</script>

<template>
  <main class="page">
    <!-- ── Header / bio ─────────────────────────────────────────── -->
    <header class="intro">
      <p class="eyebrow">{{ profile.location }}</p>
      <h1 class="name">{{ profile.name }}</h1>
      <p class="role">{{ profile.role }}</p>
      <p class="bio">{{ profile.bio }}</p>
      <br>
      <p class="tail">{{ profile.tail }}</p>
      <nav class="links">
        <a
          v-for="link in profile.links"
          :key="link.label"
          :href="link.url"
          class="link"
        >{{ link.label }}</a>
      </nav>
    </header>

    <!-- ── Ornament ──────────────────────────────────────────────── -->
    <div class="ornament" aria-hidden="true">❧</div>

    <!-- ── Portfolio ────────────────────────────────────────────── -->
    <section class="work">
      <h2 class="section-label">Selected Work</h2>
      <ul class="projects">
        <li
          v-for="(project, i) in projects"
          :key="project.title"
          class="project"
          :style="{ animationDelay: `${0.08 * i}s` }"
        >
          <a :href="project.url" class="project-link">
            <span class="project-year">{{ project.year }}</span>
            <span class="project-body">
              <span class="project-title">{{ project.title }}</span>
              <span class="project-blurb">{{ project.blurb }}</span>
              <span class="project-tags">
                <span v-for="tag in project.tags" :key="tag" class="tag">{{ tag }}</span>
              </span>
            </span>
          </a>
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
  margin-top: 0.5rem;
  letter-spacing: 0.01em;
}
.bio {
  margin-top: 1.8rem;
  color: #3a382f;
  line-height: 1.78;
  font-size: 0.98rem;
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
.links {
  margin-top: 2rem;
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

/* ── Ornament ───────────────────────────────────────────────────── */
.ornament {
  text-align: center;
  color: var(--accent);
  opacity: 0.55;
  font-family: 'Fraunces', serif;
  font-size: 2rem;
  letter-spacing: 0;
  margin: clamp(3rem, 8vw, 5.5rem) 0 0;
  user-select: none;
}

/* ── Work ───────────────────────────────────────────────────────── */
.work { margin-top: 2rem; }
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
.project-link:hover {
  background: rgba(184, 71, 42, 0.04);
  padding-left: 1rem;
}

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
.project-link:hover .project-title { color: var(--accent); }
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

@media (max-width: 480px) {
  .project-link { grid-template-columns: 1fr; gap: 0.5rem; }
  .project-year { padding-top: 0; }
  .bio::first-letter { float: none; font-size: 1em; color: inherit; padding-top: 0; }
}
</style>

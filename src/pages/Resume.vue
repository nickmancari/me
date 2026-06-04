<script setup>
const contact = [
  { label: 'Email',  url: 'mailto:nickjmancari@gmail.com' },
  { label: 'GitHub', url: 'https://github.com/nickmancari' },
  { label: 'Phone',  url: 'tel:+13023735563' },
]

const summary =
  `Software engineer with 4+ years building and shipping full-stack production systems in ` +
  `Ruby on Rails, Vue.js, and MongoDB, including LLM-powered features from integration through ` +
  `production rollout. Backed by a decade in technical support and systems, giving me unusually ` +
  `deep product, debugging, and customer insight. I own features end-to-end — architecture, ` +
  `test coverage, deployment, and the messy production realities most engineers only see secondhand.`

const experience = [
  {
    company: 'CipherHealth',
    location: 'Remote · New York City, NY',
    roles: [
      {
        title: 'Software Engineer',
        period: 'Aug 2024 – Present',
        points: [
          'Architect and maintain scalable, production-grade code backed by comprehensive test coverage for long-term reliability.',
          'Build and ship full-stack features across the entire application layer with Ruby on Rails, MongoDB, and Vue.js.',
          'Develop and ship LLM-powered features end-to-end — from model integration and prompt engineering to production rollout — adding AI-driven capabilities to the product.',
          'Own and operate CI/CD smoke-test suites supporting integration validation across deployment pipelines.',
          'Optimize MongoDB queries and data-retrieval strategies, improving application performance and response efficiency.',
          'Drive bug-fix initiatives end-to-end, from defect identification to resolution, reducing friction and elevating the user experience.',
          'Deploy and manage containerized services with Docker and Kubernetes for scalable, consistent environments across development and production.',
        ],
      },
      {
        title: 'Senior Technical Support Engineer',
        period: 'Jul 2022 – Aug 2024',
        points: [
          'Served as an escalation point for complex technical issues, interfacing between customer support teams and developers.',
          'Conducted regression testing, bug fixes, and unit tests, and authored documentation to guide configuration improvements.',
          'Used Ruby on Rails, JavaScript, and MongoDB to enhance application performance and resolve defects.',
          'Performed database querying to provide impact analysis of bugs and incidents.',
          'Constructed Rails migrations for mass bug fixes requiring extensive efficiency.',
          'Collaborated on pull requests, conducted code reviews, and provided feedback to optimize development processes.',
        ],
      },
    ],
  },
  {
    company: 'Cloudflare',
    location: 'Remote · Austin, TX',
    roles: [
      {
        title: 'Technical Support Engineer',
        period: 'Aug 2021 – Jul 2022',
        points: [
          'Resolved customer issues across networking, DNS, CDN, and serverless infrastructure using JavaScript and Rust (Cloudflare Workers).',
          'Maintained and established strong internal documentation to streamline shared knowledge.',
          'Analyzed traffic data with Elasticsearch and Grafana, improving system responses and client network operations.',
          'Developed custom Bash scripts and tools, enhancing troubleshooting capabilities and support quality.',
        ],
      },
    ],
  },
  {
    company: 'Ochiltree General Hospital',
    location: 'Perryton, TX',
    roles: [
      {
        title: 'Computer Information Systems Technician',
        period: 'Oct 2017 – Aug 2021',
        points: [
          'Managed IT operations, supporting electronic medical records systems for a wide array of doctors, nurses, and administrators.',
          'Administered network security measures, including VPNs, VLANs, and HIPAA compliance.',
          'Spearheaded development of a web application for employee onboarding; recognized as Employee of the Month in November 2019.',
        ],
      },
    ],
  },
  {
    company: 'Pampa Independent School District',
    location: 'Pampa, TX',
    roles: [
      {
        title: 'District Technology Specialist',
        period: 'Aug 2014 – Oct 2017',
        points: [
          'Oversaw technology support for 3,000 users and maintained 7,000 devices across multiple platforms.',
          'Led deployment of AirWatch MDM and established a macOS X Server in a predominantly Windows environment.',
        ],
      },
    ],
  },
]

const education = {
  school: 'Southern New Hampshire University',
  degree: 'Associate of Science, Computer Science',
  period: '2021 – 2023',
}

const skills = [
  { label: 'Languages',          items: ['Ruby', 'JavaScript', 'Python', 'Go', 'Bash'] },
  { label: 'Frameworks & Tools', items: ['Ruby on Rails', 'Vue', 'Sass', 'MVC', 'Nginx', 'PostgreSQL', 'Git'] },
  { label: 'Systems',            items: ['Linux', 'macOS', 'Windows', 'ChromeOS', 'BSD'] },
  { label: 'Networking',         items: ['DNS', 'CDN', 'VPN', 'VLAN'] },
  { label: 'Databases',          items: ['Snowflake', 'MongoDB', 'PostgreSQL'] },
  { label: 'Ticketing & Org',    items: ['Salesforce', 'JIRA', 'Confluence'] },
  { label: 'Machine Learning / AI', items: ['MCP', 'Gemini', 'Ollama', 'Qwen'] },
  { label: 'Other',              items: ['BugSnag', 'DataDog', 'Hyper-V', 'ESXi', 'LVM', 'DigitalOcean'] },
]

const isExternal = (url) => /^https?:\/\//.test(url)
</script>

<template>
  <main id="main" class="page">
    <!-- ── Header ───────────────────────────────────────────────── -->
    <header class="intro">
      <p class="eyebrow">Resume</p>
      <h1 class="name">Nick Mancari</h1>
      <p class="role">Software Engineer</p>

      <div class="bio-block">
        <p class="bio">{{ summary }}</p>
      </div>

      <nav class="links" aria-label="Contact">
        <a
          v-for="link in contact"
          :key="link.label"
          :href="link.url"
          class="link"
          :target="isExternal(link.url) ? '_blank' : null"
          :rel="isExternal(link.url) ? 'noopener noreferrer' : null"
        >{{ link.label }}<span v-if="isExternal(link.url)" class="link-ext" aria-hidden="true">↗</span></a>
        <a class="resume-download" href="/nick-mancari-resume.pdf" download>
          Download PDF
        </a>
      </nav>
    </header>

    <div class="ornament" aria-hidden="true">❧</div>

    <!-- ── Experience ───────────────────────────────────────────── -->
    <section class="rsection" aria-labelledby="experience-label">
      <h2 id="experience-label" class="section-label">Experience</h2>
      <article v-for="job in experience" :key="job.company" class="xp">
        <header class="xp-head">
          <h3 class="xp-company">{{ job.company }}</h3>
          <span class="xp-location">{{ job.location }}</span>
        </header>
        <div v-for="role in job.roles" :key="role.title" class="xp-role">
          <div class="xp-period">{{ role.period }}</div>
          <div class="xp-detail">
            <h4 class="xp-title">{{ role.title }}</h4>
            <ul class="xp-points">
              <li v-for="(point, i) in role.points" :key="i">{{ point }}</li>
            </ul>
          </div>
        </div>
      </article>
    </section>

    <!-- ── Education ────────────────────────────────────────────── -->
    <section class="rsection" aria-labelledby="education-label">
      <h2 id="education-label" class="section-label">Education</h2>
      <div class="edu">
        <div class="xp-period">{{ education.period }}</div>
        <div class="xp-detail">
          <h3 class="edu-school">{{ education.school }}</h3>
          <p class="edu-degree">{{ education.degree }}</p>
        </div>
      </div>
    </section>

    <!-- ── Skills ───────────────────────────────────────────────── -->
    <section class="rsection" aria-labelledby="skills-label">
      <h2 id="skills-label" class="section-label">Technical Skills</h2>
      <dl class="skills">
        <div v-for="group in skills" :key="group.label" class="skill-group">
          <dt class="skill-label">{{ group.label }}</dt>
          <dd class="skill-items">
            <span v-for="item in group.items" :key="item" class="tag">{{ item }}</span>
          </dd>
        </div>
      </dl>
    </section>

    <footer class="footer">
      <p>© {{ new Date().getFullYear() }} Nick Mancari</p>
    </footer>
  </main>
</template>

<style>
/* Reuses global primitives from Home.vue (.page, .intro, .eyebrow, .name,
   .role, .links, .link, .link-ext, .ornament, .section-label, .tag, .footer). */

.rsection { margin-top: 3rem; }
/* First section follows the ornament, which already supplies the gap. */
.rsection:first-of-type { margin-top: 0; }

/* ── Download button ────────────────────────────────────────────── */
.resume-download {
  font-family: 'Lora', serif;
  font-size: 0.85rem;
  letter-spacing: 0.02em;
  color: var(--accent);
  text-decoration: none;
  padding: 0.4rem 0.95rem;
  border: 1px solid rgba(184, 71, 42, 0.4);
  border-radius: 3px;
  background: rgba(184, 71, 42, 0.06);
  transition: background 0.18s, border-color 0.18s, color 0.18s;
}
.resume-download:hover {
  background: var(--accent);
  border-color: var(--accent);
  color: var(--paper);
}

/* ── Experience ─────────────────────────────────────────────────── */
.xp {
  padding: 1.8rem 0;
  border-bottom: 1px solid var(--rule);
}
.xp:last-of-type { border-bottom: none; }
.xp-head {
  display: flex;
  flex-wrap: wrap;
  align-items: baseline;
  gap: 0.3rem 0.9rem;
  margin-bottom: 1.2rem;
}
.xp-company {
  font-family: 'Fraunces', serif;
  font-variation-settings: 'opsz' 48;
  font-weight: 600;
  font-size: 1.4rem;
  letter-spacing: -0.01em;
}
.xp-location {
  font-family: 'Lora', serif;
  font-style: italic;
  font-size: 0.88rem;
  color: var(--muted);
}

.xp-role,
.edu {
  display: grid;
  grid-template-columns: 8.5rem 1fr;
  gap: 1.4rem;
}
.xp-role + .xp-role { margin-top: 1.6rem; }

.xp-period {
  font-size: 0.83rem;
  color: var(--muted);
  padding-top: 0.35rem;
  font-variant-numeric: oldstyle-nums;
  letter-spacing: 0.01em;
}
.xp-title {
  font-family: 'Fraunces', serif;
  font-style: italic;
  font-variation-settings: 'opsz' 36;
  font-weight: 500;
  font-size: 1.12rem;
  color: var(--accent);
  margin-bottom: 0.7rem;
}
.xp-points {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
}
.xp-points li {
  position: relative;
  padding-left: 1.1rem;
  color: #4a473e;
  font-size: 0.93rem;
  line-height: 1.62;
}
.xp-points li::before {
  content: '—';
  position: absolute;
  left: 0;
  color: var(--accent);
  opacity: 0.65;
}

/* ── Education ──────────────────────────────────────────────────── */
.edu-school {
  font-family: 'Fraunces', serif;
  font-variation-settings: 'opsz' 36;
  font-weight: 600;
  font-size: 1.12rem;
}
.edu-degree {
  margin-top: 0.3rem;
  color: #4a473e;
  font-size: 0.93rem;
}

/* ── Skills ─────────────────────────────────────────────────────── */
.skills {
  margin-top: 0.4rem;
  display: flex;
  flex-direction: column;
}
.skill-group {
  display: grid;
  grid-template-columns: 8.5rem 1fr;
  gap: 1.4rem;
  padding: 1.05rem 0;
  border-bottom: 1px solid var(--rule);
}
.skill-group:last-child { border-bottom: none; }
.skill-label {
  font-size: 0.73rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--muted);
  padding-top: 0.3rem;
}
.skill-items {
  display: flex;
  flex-wrap: wrap;
  gap: 0.45rem;
}

@media (max-width: 560px) {
  .xp-role,
  .edu,
  .skill-group {
    grid-template-columns: 1fr;
    gap: 0.5rem;
  }
  .xp-period { padding-top: 0; }
  .skill-label { padding-top: 0; padding-bottom: 0.2rem; }
}
</style>

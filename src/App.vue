<script setup lang="ts">
type Project = {
  name: string
  description: string
  link: string
  stack: string
  status: 'Live' | 'Alpha' | 'WIP'
}

const projects: Project[] = [
  {
    name: 'Conclave',
    description:
      'AI decision memos you can challenge in chat and revise without losing the original. Bring your own provider key or try the free NVIDIA model.',
    link: 'https://conclave.click',
    stack: 'React · TypeScript · AI SDK',
    status: 'Live',
  },
  {
    name: 'Pulse',
    description:
      'Voice feedback via QR codes, with transcription and sentiment baked in.',
    link: 'https://pulseapp.click',
    stack: 'React · Voice AI',
    status: 'Live',
  },
  {
    name: 'Shopify Policy',
    description:
      'Paste a store URL. It reads shipping and returns pages, streams progress, and turns the fine print into a summary you can ask questions against.',
    link: 'https://shopify.glamboyosa.xyz',
    stack: 'Next.js · Shopify · SSE',
    status: 'Live',
  },
  {
    name: 'Swig',
    description:
      'PostgreSQL job queue for Go: transactional enqueue, leader election, batch processing.',
    link: 'https://swig.glamboyosa.xyz',
    stack: 'Go · PostgreSQL',
    status: 'Alpha',
  },
  {
    name: 'Ore',
    description: 'TypeScript helpers for streaming and Server-Sent Events.',
    link: 'https://www.npmjs.com/package/@glamboyosa/ore',
    stack: 'TypeScript',
    status: 'Live',
  },
  {
    name: 'Ore-pper',
    description: 'Copy-paste React stepper. Tailwind and Framer Motion.',
    link: 'https://ore-pper.glamboyosa.xyz',
    stack: 'React · Tailwind',
    status: 'Live',
  },
  {
    name: 'Loom',
    description:
      'Local file-watching workflow runner. GitHub Actions, without GitHub.',
    link: 'https://github.com/glamboyosa/loom',
    stack: 'Elixir · Docker',
    status: 'WIP',
  },
  {
    name: 'Animations',
    description: 'Recreations and motion experiments.',
    link: 'https://animations.glamboyosa.xyz',
    stack: 'Framer Motion',
    status: 'Live',
  },
]
</script>

<template>
  <div class="page">
    <header class="header">
      <h1 class="title">Things</h1>
      <p class="lede">
        Side projects and experiments by Osa. Some shipped, some still on the
        bench.
      </p>
    </header>

    <main>
      <ul class="list">
        <li v-for="project in projects" :key="project.name">
          <a
            class="row"
            :href="project.link"
            target="_blank"
            rel="noopener noreferrer"
          >
            <div class="row-top">
              <h2 class="name">{{ project.name }}</h2>
              <span class="status" :data-status="project.status">{{
                project.status
              }}</span>
            </div>
            <p class="description">{{ project.description }}</p>
            <div class="row-meta">
              <span class="stack">{{ project.stack }}</span>
              <span class="arrow" aria-hidden="true">↗</span>
            </div>
          </a>
        </li>
      </ul>
    </main>

    <footer class="footer">
      <a href="https://glamboyosa.xyz">glamboyosa.xyz</a>
      <a href="https://github.com/glamboyosa">GitHub</a>
    </footer>
  </div>
</template>

<style>
.page {
  --bg: oklch(0.975 0.006 250);
  --ink: oklch(0.22 0.025 255);
  --muted: oklch(0.48 0.02 255);
  --line: oklch(0.88 0.012 255);
  --accent: oklch(0.48 0.11 195);
  --accent-soft: oklch(0.94 0.02 195);
  --live: oklch(0.45 0.1 155);
  --wip: oklch(0.52 0.08 75);
  --font-weight-normal: 400;
  --font-weight-medium: 500;
  --font-weight-semibold: 600;
  --ease-out: cubic-bezier(0.2, 0, 0, 1);
  --duration: 150ms;

  min-height: 100vh;
  min-height: 100dvh;
  background: var(--bg);
  color: var(--ink);
  font-family: 'IBM Plex Sans', system-ui, sans-serif;
  font-synthesis: none;
  padding:
    max(3rem, env(safe-area-inset-top))
    max(1.25rem, env(safe-area-inset-right))
    max(4rem, env(safe-area-inset-bottom))
    max(1.25rem, env(safe-area-inset-left));
}

@media (min-width: 768px) {
  .page {
    padding:
      max(5rem, env(safe-area-inset-top))
      max(2rem, env(safe-area-inset-right))
      max(6rem, env(safe-area-inset-bottom))
      max(2rem, env(safe-area-inset-left));
  }
}

.page ::selection {
  background: color-mix(in oklch, var(--accent) 22%, transparent);
  color: var(--ink);
}

.header {
  max-width: 40rem;
  margin: 0 auto 3.5rem;
}

.title {
  margin: 0 0 0.85rem;
  font-family: Newsreader, Georgia, serif;
  font-optical-sizing: auto;
  font-size: clamp(3.25rem, 10vw, 5rem);
  font-weight: var(--font-weight-semibold);
  line-height: 1.05;
  letter-spacing: -0.02em;
  text-wrap: balance;
  color: var(--ink);
}

.lede {
  margin: 0;
  max-width: 32rem;
  font-size: 1.125rem;
  font-weight: var(--font-weight-normal);
  line-height: 1.55;
  color: var(--muted);
  text-wrap: pretty;
}

.list {
  list-style: none;
  margin: 0 auto;
  padding: 0;
  max-width: 40rem;
  border-top: 1px solid var(--line);
}

.list li {
  border-bottom: 1px solid var(--line);
}

.row {
  display: block;
  padding: 1.5rem 0.5rem;
  margin: 0 -0.5rem;
  border-radius: 0.25rem;
  text-decoration: none;
  color: inherit;
  transform-origin: center;
  transition-property: background-color, transform;
  transition-duration: var(--duration);
  transition-timing-function: var(--ease-out);
}

.row:hover {
  background: color-mix(in oklch, var(--accent-soft) 55%, transparent);
}

.row:focus {
  outline: none;
}

.row:focus-visible {
  outline: 2px solid var(--ink);
  outline-offset: 3px;
}

.row:active {
  transform: scale(0.96);
}

.row-top {
  display: flex;
  align-items: baseline;
  justify-content: space-between;
  gap: 1rem;
  margin-bottom: 0.45rem;
}

.name {
  margin: 0;
  font-size: 1.25rem;
  font-weight: var(--font-weight-semibold);
  letter-spacing: -0.015em;
  line-height: 1.2;
  text-wrap: balance;
  transition-property: color;
  transition-duration: var(--duration);
  transition-timing-function: var(--ease-out);
}

.row:hover .name,
.row:focus-visible .name {
  color: var(--accent);
}

.status {
  flex-shrink: 0;
  font-size: 0.75rem;
  font-weight: var(--font-weight-medium);
  letter-spacing: 0.06em;
  text-transform: uppercase;
  color: var(--muted);
  font-variant-numeric: tabular-nums;
  user-select: none;
}

.status[data-status='Live'] {
  color: var(--live);
}

.status[data-status='Alpha'],
.status[data-status='WIP'] {
  color: var(--wip);
}

.description {
  margin: 0 0 0.75rem;
  max-width: 36rem;
  font-size: 0.9375rem;
  line-height: 1.55;
  color: var(--muted);
  text-wrap: pretty;
}

.row-meta {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1rem;
}

.stack {
  font-size: 0.8125rem;
  letter-spacing: 0.01em;
  color: color-mix(in oklch, var(--muted) 80%, var(--ink));
}

.arrow {
  display: inline-block;
  font-size: 0.875rem;
  line-height: 1;
  color: var(--muted);
  margin-top: -1px;
  user-select: none;
  pointer-events: none;
  transition-property: color, transform;
  transition-duration: var(--duration);
  transition-timing-function: var(--ease-out);
}

.row:hover .arrow,
.row:focus-visible .arrow {
  color: var(--accent);
  transform: translate(1px, -1px);
}

.footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 1.5rem;
  max-width: 40rem;
  margin: 3.5rem auto 0;
  padding-top: 1.25rem;
  border-top: 1px solid var(--line);
  font-size: 0.875rem;
}

.footer a {
  position: relative;
  display: inline-flex;
  align-items: center;
  min-height: 2.5rem;
  color: var(--muted);
  text-decoration: none;
  text-underline-offset: 3px;
  transition-property: color;
  transition-duration: var(--duration);
  transition-timing-function: var(--ease-out);
}

.footer a::before {
  content: '';
  position: absolute;
  inset: 0 -0.35rem;
}

.footer a:hover {
  color: var(--accent);
  text-decoration: underline;
}

.footer a:focus {
  outline: none;
}

.footer a:focus-visible {
  outline: 2px solid var(--ink);
  outline-offset: 3px;
  border-radius: 0.125rem;
}

.footer a:active {
  transform: scale(0.96);
  transition-property: color, transform;
  transition-duration: var(--duration);
  transition-timing-function: var(--ease-out);
}

@media (prefers-reduced-motion: reduce) {
  .row,
  .name,
  .arrow,
  .footer a {
    transition: none;
  }

  .row:active,
  .footer a:active {
    transform: none;
  }

  .row:hover .arrow,
  .row:focus-visible .arrow {
    transform: none;
  }
}
</style>

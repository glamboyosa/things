<script setup lang="ts">
import { ref } from 'vue'

const projects = ref([
  {
    name: 'Pulse',
    description: 'Authentic voice feedback platform. Collect voice messages via QR codes with automatic transcription and sentiment analysis.',
    link: 'https://pulseapp.click',
    tags: ['SaaS', 'Voice AI', 'React'],
    status: 'Live',
    color: 'text-pink-500',
    borderColor: 'border-pink-500'
  },
  {
    name: 'Swig',
    description: 'PostgreSQL-backed job queue system for Golang. Features transactional integrity, leader election, and batch processing.',
    link: 'https://swig.glamboyosa.xyz',
    tags: ['Golang', 'System Design', 'PostgreSQL'],
    status: 'Alpha',
    color: 'text-cyan-500',
    borderColor: 'border-cyan-500'
  },
  {
    name: 'Ore',
    description: 'Modern, lightweight TypeScript library for robust streaming and Server-Sent Events (SSE) consumption.',
    link: 'https://www.npmjs.com/package/@glamboyosa/ore',
    tags: ['TypeScript', 'Library', 'Streaming'],
    status: 'v1.0.0',
    color: 'text-yellow-500',
    borderColor: 'border-yellow-500'
  },
  {
    name: 'Ore-pper',
    description: 'A copy-paste Stepper component for React apps built with Tailwind CSS and Framer Motion.',
    link: 'https://ore-pper.glamboyosa.xyz',
    tags: ['React', 'UI Component', 'Tailwind'],
    status: 'Live',
    color: 'text-purple-500',
    borderColor: 'border-purple-500'
  },
  {
    name: 'Loom',
    description: 'Local file-watching workflow runner. Think GitHub Actions, but local and file-driven.',
    link: 'https://github.com/glamboyosa/loom', 
    tags: ['Elixir', 'DevTool', 'Docker'],
    status: 'WIP',
    color: 'text-green-500',
    borderColor: 'border-green-500'
  },
  {
    name: 'Animations',
    description: 'A collection of high-quality animation recreations and experiments.',
    link: 'https://animations.glamboyosa.xyz',
    tags: ['Animation', 'Framer Motion', 'Design'],
    status: 'Live',
    color: 'text-fuchsia-500',
    borderColor: 'border-fuchsia-500'
  }
])
</script>

<template>
  <div class="min-h-screen bg-[#1a1b26] text-[#a9b1d6] font-mono selection:bg-[#7aa2f7] selection:text-[#1a1b26] p-4 md:p-12 relative overflow-hidden">
    
    <!-- CRT Overlay Effect -->
    <div class="pointer-events-none fixed inset-0 z-50 bg-[linear-gradient(rgba(18,16,16,0)_50%,rgba(0,0,0,0.25)_50%),linear-gradient(90deg,rgba(255,0,0,0.06),rgba(0,255,0,0.02),rgba(0,0,255,0.06))] bg-[length:100%_2px,3px_100%] opacity-20"></div>

    <!-- Header -->
    <header class="max-w-4xl mx-auto mb-16 md:mb-24 border-b-4 border-[#414868] pb-8">
      <h1 class="text-4xl md:text-6xl font-black mb-4 tracking-tighter text-[#7aa2f7] uppercase drop-shadow-[4px_4px_0_rgba(0,0,0,0.5)]">
        Things.exe
      </h1>
      <div class="flex flex-col md:flex-row md:justify-between md:items-end gap-4">
        <p class="text-lg md:text-xl text-[#9aa5ce] max-w-xl leading-relaxed">
          > A collection of artifacts crafted by Osa.<br>
          > <span class="animate-pulse">_</span>
        </p>
        <div class="text-xs text-[#565f89] uppercase tracking-widest border border-[#565f89] px-2 py-1">
          System: Online
        </div>
      </div>
    </header>

    <!-- Grid -->
    <main class="max-w-4xl mx-auto pb-24">
      <div class="grid grid-cols-1 gap-8">
        <a 
          v-for="project in projects" 
          :key="project.name"
          :href="project.link"
          target="_blank"
          rel="noopener noreferrer"
          class="group relative block bg-[#24283b] border-2 border-[#414868] p-6 transition-transform duration-100 hover:-translate-y-1 hover:translate-x-1 hover:shadow-[8px_8px_0_rgba(0,0,0,0.5)] active:translate-y-0 active:translate-x-0 active:shadow-none"
          :class="`hover:${project.borderColor}`"
        >
          <!-- Title Bar -->
          <div class="flex justify-between items-start mb-4 border-b-2 border-[#414868] pb-2 border-dashed">
            <h2 class="text-2xl font-bold uppercase tracking-wide" :class="project.color">
              {{ project.name }}
            </h2>
            <span 
              class="px-2 py-1 text-xs font-bold uppercase bg-[#1a1b26] border border-[#414868]"
              :class="project.status === 'Live' ? 'text-green-400' : 'text-yellow-400'"
            >
              [{{ project.status }}]
            </span>
          </div>
          
          <div class="flex flex-col md:flex-row gap-6">
            <!-- Description -->
            <p class="flex-grow text-[#c0caf5] text-sm md:text-base leading-relaxed">
              {{ project.description }}
            </p>

            <!-- Tags -->
            <div class="flex flex-wrap md:flex-col gap-2 md:w-48 md:shrink-0 justify-end">
              <span 
                v-for="tag in project.tags" 
                :key="tag"
                class="text-xs font-bold px-2 py-1 bg-[#1a1b26] text-[#7aa2f7] border border-[#414868] text-center"
              >
                #{{ tag }}
              </span>
            </div>
          </div>
          
          <!-- Corner decorations -->
          <div class="absolute -top-1 -left-1 w-2 h-2 bg-[#1a1b26] border-r border-b border-[#414868]"></div>
          <div class="absolute -top-1 -right-1 w-2 h-2 bg-[#1a1b26] border-l border-b border-[#414868]"></div>
          <div class="absolute -bottom-1 -left-1 w-2 h-2 bg-[#1a1b26] border-r border-t border-[#414868]"></div>
          <div class="absolute -bottom-1 -right-1 w-2 h-2 bg-[#1a1b26] border-l border-t border-[#414868]"></div>
        </a>
      </div>
    </main>

    <!-- Footer -->
    <footer class="max-w-4xl mx-auto border-t-4 border-[#414868] pt-8 flex justify-between items-center text-[#565f89] text-sm uppercase">
      <p>
        © 2026 
        <a href="https://glamboyosa.xyz" class="hover:text-[#7aa2f7] hover:underline decoration-2 underline-offset-4 font-bold">
          GLAMBOYOSA
        </a>
      </p>
      <div class="flex gap-4 font-bold">
        <a href="https://github.com/glamboyosa" class="hover:text-[#7aa2f7] hover:underline decoration-2 underline-offset-4">[GitHub]</a>
        <a href="https://twitter.com/glamboyosa" class="hover:text-[#7aa2f7] hover:underline decoration-2 underline-offset-4">[Twitter]</a>
      </div>
    </footer>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;700;800&display=swap');

:root {
  font-family: 'JetBrains Mono', monospace;
}

body {
  background-color: #1a1b26;
}

/* Custom Scrollbar */
::-webkit-scrollbar {
  width: 12px;
}

::-webkit-scrollbar-track {
  background: #1a1b26; 
}

::-webkit-scrollbar-thumb {
  background: #414868; 
  border: 2px solid #1a1b26;
}

::-webkit-scrollbar-thumb:hover {
  background: #565f89; 
}
</style>

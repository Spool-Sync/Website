<template>
  <section id="get-started" class="cta-section">
    <div class="container">
      <div class="cta-card reveal">
        <!-- Gradient border glow -->
        <div class="cta-glow" aria-hidden="true"></div>

        <div class="cta-inner">
          <div class="cta-text">
            <p class="section-label">Get started</p>
            <h2 class="cta-title">
              Never run out of filament<br />
              <span class="gradient-text">mid-print again.</span>
            </h2>
            <p class="cta-desc">
              Self-hosted, open-source, and built for makers who take their
              filament seriously. Deploy in under five minutes.
            </p>

            <div class="cta-actions">
              <a href="https://github.com/Spool-Sync/SpoolSync-App" target="_blank" rel="noopener" class="btn btn-primary">
                <svg width="16" height="16" viewBox="0 0 16 16" fill="currentColor">
                  <path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/>
                </svg>
                Clone on GitHub
              </a>
              <a href="#how-it-works" class="btn btn-ghost">Read the docs</a>
            </div>
          </div>

          <div class="cta-commands">
            <div class="cmd-step">
              <span class="cmd-label">01 — Clone</span>
              <div class="code-block">
                <span class="prompt">$</span>
                <code>git clone https://github.com/Spool-Sync/SpoolSync-App</code>
                <button class="copy-btn" @click="copy('git clone https://github.com/Spool-Sync/SpoolSync-App', 0)" :title="copied[0] ? 'Copied' : 'Copy'">
                  <svg v-if="!copied[0]" width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="9" y="9" width="13" height="13" rx="2"/><path d="M5 15H4a2 2 0 01-2-2V4a2 2 0 012-2h9a2 2 0 012 2v1"/></svg>
                  <svg v-else width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="#51cf66" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M20 6L9 17l-5-5"/></svg>
                </button>
              </div>
            </div>

            <div class="cmd-step">
              <span class="cmd-label">02 — Configure</span>
              <div class="code-block">
                <span class="prompt">$</span>
                <code>cp .env.example .env</code>
                <button class="copy-btn" @click="copy('cp .env.example .env', 1)" :title="copied[1] ? 'Copied' : 'Copy'">
                  <svg v-if="!copied[1]" width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="9" y="9" width="13" height="13" rx="2"/><path d="M5 15H4a2 2 0 01-2-2V4a2 2 0 012-2h9a2 2 0 012 2v1"/></svg>
                  <svg v-else width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="#51cf66" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M20 6L9 17l-5-5"/></svg>
                </button>
              </div>
            </div>

            <div class="cmd-step">
              <span class="cmd-label">03 — Launch</span>
              <div class="code-block">
                <span class="prompt">$</span>
                <code>docker compose up -d</code>
                <button class="copy-btn" @click="copy('docker compose up -d', 2)" :title="copied[2] ? 'Copied' : 'Copy'">
                  <svg v-if="!copied[2]" width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="9" y="9" width="13" height="13" rx="2"/><path d="M5 15H4a2 2 0 01-2-2V4a2 2 0 012-2h9a2 2 0 012 2v1"/></svg>
                  <svg v-else width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="#51cf66" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M20 6L9 17l-5-5"/></svg>
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const copied = ref([false, false, false])

async function copy(text, idx) {
  await navigator.clipboard.writeText(text)
  copied.value[idx] = true
  setTimeout(() => { copied.value[idx] = false }, 2000)
}
</script>

<style scoped>
.cta-section {
  padding: 60px 0 120px;
}

.cta-card {
  position: relative;
  border-radius: var(--radius-xl);
  overflow: hidden;
  background: var(--card);
  border: 1px solid var(--border);
}

.cta-glow {
  position: absolute;
  inset: -1px;
  border-radius: inherit;
  background: var(--gradient);
  opacity: 0.15;
  filter: blur(1px);
  pointer-events: none;
}

.cta-inner {
  position: relative;
  z-index: 1;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  padding: 60px;
  align-items: center;
}

.cta-title {
  font-size: clamp(26px, 3.5vw, 42px);
  font-weight: 800;
  line-height: 1.12;
  letter-spacing: -0.025em;
  margin-bottom: 16px;
}

.cta-desc {
  font-size: 15px;
  line-height: 1.7;
  color: var(--text-muted);
  margin-bottom: 32px;
}

.cta-actions {
  display: flex;
  gap: 14px;
  flex-wrap: wrap;
}

.cta-commands {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.cmd-step { display: flex; flex-direction: column; gap: 8px; }

.cmd-label {
  font-size: 10px;
  font-weight: 700;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--text-dim);
}

.code-block {
  position: relative;
  padding-right: 40px;
}

.copy-btn {
  position: absolute;
  right: 10px;
  top: 50%;
  transform: translateY(-50%);
  background: none;
  border: none;
  cursor: pointer;
  color: var(--text-muted);
  padding: 4px;
  border-radius: 4px;
  transition: color 0.2s;
  display: flex;
  align-items: center;
}
.copy-btn:hover { color: var(--text); }

@media (max-width: 900px) {
  .cta-inner { grid-template-columns: 1fr; gap: 40px; padding: 40px 32px; }
}

@media (max-width: 560px) {
  .cta-section { padding: 40px 0 80px; }
  .cta-inner { padding: 32px 24px; }
}
</style>

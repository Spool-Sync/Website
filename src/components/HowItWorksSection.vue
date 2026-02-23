<template>
  <section id="how-it-works" class="hiw-section">
    <!-- Background accent -->
    <div class="hiw-bg" aria-hidden="true"></div>

    <div class="container">
      <div class="section-header reveal">
        <p class="section-label">How it works</p>
        <h2 class="section-title">Up and running in minutes</h2>
        <p class="section-subtitle">
          SpoolSync is designed for makers, not sysadmins.
          Deploy it, plug in your hardware, and start tracking.
        </p>
      </div>

      <div class="steps">
        <div
          v-for="(step, i) in steps"
          :key="step.title"
          :class="['step', 'reveal', `reveal-delay-${i + 1}`]"
        >
          <div class="step-number-wrap">
            <div class="step-number">{{ String(i + 1).padStart(2, '0') }}</div>
            <div v-if="i < steps.length - 1" class="step-connector"></div>
          </div>
          <div class="step-content">
            <div class="step-icon" v-html="step.icon"></div>
            <h3 class="step-title">{{ step.title }}</h3>
            <p class="step-desc">{{ step.description }}</p>
            <div v-if="step.code" class="code-block">
              <span class="prompt">$</span>
              <code>{{ step.code }}</code>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const steps = [
  {
    icon: `<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="3" width="20" height="14" rx="2"/><path d="M8 21h8M12 17v4"/></svg>`,
    title: 'Deploy in one command',
    description: 'Clone the repository and spin up the full stack with Docker Compose. PostgreSQL, backend, and frontend all come pre-configured.',
    code: 'docker compose up -d',
  },
  {
    icon: `<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="5" r="3"/><path d="M6.5 8a2.5 2.5 0 00-2.45 3l1.5 6A2.5 2.5 0 008 19h.5"/><path d="M17.5 8a2.5 2.5 0 012.45 3l-1.5 6A2.5 2.5 0 0116 19h-.5"/><path d="M8 19h8"/></svg>`,
    title: 'Flash your ESP32 scales',
    description: 'Upload the open-source firmware to any ESP32 with a HX711 load cell. Provision it over USB with the built-in Web Serial wizard.',
  },
  {
    icon: `<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M20 12V22H4V12"/><path d="M22 7H2v5h20V7z"/><path d="M12 22V7"/><path d="M12 7H7.5a2.5 2.5 0 010-5C11 2 12 7 12 7z"/><path d="M12 7h4.5a2.5 2.5 0 000-5C13 2 12 7 12 7z"/></svg>`,
    title: 'Add your spools',
    description: 'Tap an NFC tag, place a spool on the scale, or manually enter the details. SpoolSync ingests from the Open Filament Database automatically.',
  },
  {
    icon: `<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M22 12h-4l-3 9L9 3l-3 9H2"/></svg>`,
    title: 'Monitor everything',
    description: 'Watch weights update live as prints run. Get notified when stock runs low. Check print job status across all connected printers.',
  },
]
</script>

<style scoped>
.hiw-section {
  padding: 120px 0;
  position: relative;
}

.hiw-bg {
  position: absolute;
  inset: 0;
  background: radial-gradient(ellipse 60% 50% at 50% 50%, rgba(102, 153, 255, 0.04) 0%, transparent 70%);
  pointer-events: none;
}

.section-header {
  margin-bottom: 72px;
}

.steps {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 0;
  position: relative;
}

.step {
  display: flex;
  flex-direction: column;
  padding: 0 24px;
  position: relative;
}

.step:first-child { padding-left: 0; }
.step:last-child  { padding-right: 0; }

.step-number-wrap {
  display: flex;
  align-items: center;
  margin-bottom: 24px;
}

.step-number {
  font-size: 13px;
  font-weight: 700;
  font-family: 'JetBrains Mono', monospace;
  background: var(--gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  width: 36px;
  height: 36px;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  background-clip: unset;
  -webkit-text-fill-color: unset;
  background: var(--surface);
  border: 1px solid var(--border);
  color: var(--primary);
  flex-shrink: 0;
}

.step-connector {
  flex: 1;
  height: 1px;
  background: linear-gradient(90deg, var(--border) 0%, transparent 100%);
  margin-left: 12px;
}

.step-icon {
  color: var(--primary);
  margin-bottom: 14px;
}

.step-title {
  font-size: 15px;
  font-weight: 700;
  color: var(--text);
  margin-bottom: 10px;
  letter-spacing: -0.01em;
}

.step-desc {
  font-size: 13.5px;
  line-height: 1.65;
  color: var(--text-muted);
  margin-bottom: 14px;
}

.code-block {
  margin-top: auto;
}

@media (max-width: 900px) {
  .steps {
    grid-template-columns: 1fr 1fr;
    gap: 40px;
  }
  .step { padding: 0; }
  .step-connector { display: none; }
  .hiw-section { padding: 80px 0; }
}

@media (max-width: 560px) {
  .steps { grid-template-columns: 1fr; gap: 32px; }
}
</style>

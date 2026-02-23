<template>
  <section class="hero">
    <!-- Background grid -->
    <div class="hero-grid" aria-hidden="true"></div>

    <!-- Glow orbs -->
    <div class="orb orb-1" aria-hidden="true"></div>
    <div class="orb orb-2" aria-hidden="true"></div>

    <div class="container hero-inner">
      <!-- Left: text + CTAs -->
      <div class="hero-text">
        <div class="hero-badge reveal">
          <span class="badge-dot"></span>
          Open-source · Self-hosted · Real-time
        </div>

        <h1 class="hero-title reveal reveal-delay-1">
          Filament management<br />
          <span class="gradient-text">done right.</span>
        </h1>

        <p class="hero-subtitle reveal reveal-delay-2">
          Track every spool by weight, scan NFC tags, monitor your printers, and
          stay ahead of shortages — all from a single self-hosted dashboard.
        </p>

        <div class="hero-actions reveal reveal-delay-3">
          <a href="#get-started" class="btn btn-primary">
            <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
              <path d="M3 8h10M9 4l4 4-4 4" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
            Get Started Free
          </a>
          <a href="https://github.com/Spool-Sync/SpoolSync-App" target="_blank" rel="noopener" class="btn btn-ghost">
            <svg width="16" height="16" viewBox="0 0 16 16" fill="currentColor">
              <path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/>
            </svg>
            View on GitHub
          </a>
        </div>
      </div>

      <!-- Right: real app screenshot -->
      <div class="hero-visual reveal reveal-delay-2">
        <div class="app-frame">
          <div class="frame-bar">
            <div class="frame-dots"><span></span><span></span><span></span></div>
            <span class="frame-url">spoolsync.local / filament</span>
            <div class="live-badge">
              <span class="live-dot"></span>
              Live
            </div>
          </div>
          <img src="/screenshots/spools.png" alt="SpoolSync filament inventory" class="frame-screenshot" />
        </div>
      </div>
    </div>

    <!-- Scroll hint -->
    <div class="scroll-hint reveal">
      <div class="scroll-line"></div>
      <span>Scroll to explore</span>
    </div>
  </section>
</template>

<script setup>
</script>

<style scoped>
.hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  overflow: hidden;
  padding-top: 68px;
}

.hero-grid {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(var(--border-dim) 1px, transparent 1px),
    linear-gradient(90deg, var(--border-dim) 1px, transparent 1px);
  background-size: 60px 60px;
  mask-image: radial-gradient(ellipse 80% 60% at 50% 0%, black 30%, transparent 100%);
  animation: grid-fade 1.2s ease forwards;
}

.orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(80px);
  pointer-events: none;
}

.orb-1 {
  width: 600px;
  height: 600px;
  background: radial-gradient(circle, rgba(102, 153, 255, 0.12) 0%, transparent 70%);
  top: -100px;
  left: -200px;
}

.orb-2 {
  width: 500px;
  height: 500px;
  background: radial-gradient(circle, rgba(153, 102, 255, 0.1) 0%, transparent 70%);
  top: 100px;
  right: -150px;
}

.hero-inner {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 80px;
  align-items: center;
  flex: 1;
  padding-top: 80px;
  padding-bottom: 80px;
  position: relative;
  z-index: 1;
}

.hero-badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  background: var(--primary-dim);
  border: 1px solid rgba(102, 153, 255, 0.25);
  border-radius: 100px;
  padding: 6px 14px;
  font-size: 12px;
  font-weight: 500;
  color: var(--primary);
  margin-bottom: 24px;
}

.badge-dot {
  width: 6px;
  height: 6px;
  background: var(--primary);
  border-radius: 50%;
  animation: pulse-ring 2s ease infinite;
}

.hero-title {
  font-size: clamp(38px, 5.5vw, 68px);
  font-weight: 900;
  line-height: 1.08;
  letter-spacing: -0.03em;
  margin-bottom: 20px;
}

.hero-subtitle {
  font-size: 17px;
  line-height: 1.7;
  color: var(--text-muted);
  max-width: 480px;
  margin-bottom: 36px;
}

.hero-actions {
  display: flex;
  gap: 14px;
  flex-wrap: wrap;
}

/* App screenshot frame */
.hero-visual {
  display: flex;
  justify-content: center;
  animation: float 6s ease-in-out infinite;
}

.app-frame {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  width: 100%;
  overflow: hidden;
  box-shadow:
    0 0 0 1px rgba(102, 153, 255, 0.08),
    0 24px 80px rgba(0, 0, 0, 0.6),
    var(--glow);
}

.frame-bar {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 11px 16px;
  background: var(--surface);
  border-bottom: 1px solid var(--border-dim);
}

.frame-dots {
  display: flex;
  gap: 5px;
  flex-shrink: 0;
}
.frame-dots span {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: var(--border);
}

.frame-url {
  font-size: 11px;
  color: var(--text-dim);
  font-family: 'JetBrains Mono', monospace;
  flex: 1;
}

.live-badge {
  display: flex;
  align-items: center;
  gap: 5px;
  font-size: 11px;
  font-weight: 600;
  color: #51cf66;
  background: rgba(81, 207, 102, 0.1);
  border: 1px solid rgba(81, 207, 102, 0.2);
  border-radius: 100px;
  padding: 3px 9px;
  flex-shrink: 0;
}

.live-dot {
  width: 5px;
  height: 5px;
  background: #51cf66;
  border-radius: 50%;
  animation: pulse-ring 2s ease infinite;
}

.frame-screenshot {
  width: 100%;
  display: block;
}

/* Scroll hint */
.scroll-hint {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  padding-bottom: 36px;
  color: var(--text-dim);
  font-size: 11px;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  position: relative;
  z-index: 1;
}

.scroll-line {
  width: 1px;
  height: 36px;
  background: linear-gradient(to bottom, transparent, var(--text-dim));
}

@media (max-width: 900px) {
  .hero-inner {
    grid-template-columns: 1fr;
    gap: 48px;
    text-align: center;
    padding-top: 60px;
  }
  .hero-subtitle { margin: 0 auto 36px; }
  .hero-actions { justify-content: center; }
  .hero-visual { animation: none; }
  .scroll-hint { display: none; }
}
</style>

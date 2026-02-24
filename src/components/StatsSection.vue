<template>
  <section class="stats-section" aria-labelledby="stats-title">
    <div class="container">
      <h2 id="stats-title" class="visually-hidden">Key Statistics</h2>
      <div class="stats-grid">
        <div
          v-for="(stat, i) in stats"
          :key="stat.label"
          :class="['stat-item', 'reveal', `reveal-delay-${i + 1}`]"
        >
          <div class="stat-value gradient-text" tabindex="0">
            {{ stat.value }}
          </div>
          <div class="stat-label">{{ stat.label }}</div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const stats = [
  { value: "100+", label: "Filament brands tracked" },
  { value: "Live", label: "Real-time weight updates" },
  { value: "NFC", label: "Tap-to-identify spools" },
  { value: "100%", label: "Self-hosted & private" },
];
</script>

<style scoped>
.stats-section {
  border-top: 1px solid var(--border);
  border-bottom: 1px solid var(--border);
  background: linear-gradient(180deg, var(--surface) 0%, transparent 100%);
  padding: 56px 0;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 1px;
  background: var(--border);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  overflow: hidden;
}

.stat-item {
  background: var(--surface);
  padding: 36px 28px;
  text-align: center;
  transition: background 0.2s;
}

.stat-item:hover {
  background: var(--card);
}

.stat-value {
  font-size: 36px;
  font-weight: 900;
  letter-spacing: -0.03em;
  line-height: 1;
  margin-bottom: 8px;
}

.stat-label {
  font-size: 13px;
  color: var(--text-muted);
  font-weight: 500;
}

@media (max-width: 720px) {
  .stats-grid {
    grid-template-columns: 1fr 1fr;
  }
}

@media (max-width: 440px) {
  .stats-grid {
    grid-template-columns: 1fr;
  }
}

.visually-hidden {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}
</style>

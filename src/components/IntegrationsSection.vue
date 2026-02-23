<template>
  <section id="integrations" class="integrations-section">
    <div class="container">
      <div class="section-header reveal">
        <p class="section-label">Integrations</p>
        <h2 class="section-title">Works with your existing setup</h2>
        <p class="section-subtitle">
          SpoolSync connects to the hardware and platforms you already use —
          no proprietary ecosystem required.
        </p>
      </div>

      <div class="integrations-grid">
        <div
          v-for="(item, i) in integrations"
          :key="item.name"
          :class="['integration-card', 'reveal', `reveal-delay-${(i % 4) + 1}`]"
        >
          <div class="integration-icon" :style="{ color: item.color }" v-html="item.icon"></div>
          <div class="integration-info">
            <div class="integration-name">{{ item.name }}</div>
            <div class="integration-desc">{{ item.desc }}</div>
          </div>
          <div class="integration-badge" :style="{ background: item.color + '18', color: item.color, borderColor: item.color + '30' }">
            {{ item.badge }}
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const integrations = [
  {
    name: 'OpenPrintTag',
    desc: 'Auto-fill spool data by tapping Prusament and compatible NFC-tagged spools with your phone.',
    badge: 'NFC',
    color: '#6699ff',
    icon: `<svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="5" width="20" height="14" rx="2"/><path d="M2 10h20"/></svg>`,
  },
  {
    name: 'PrusaLink',
    desc: 'Poll print job status and nozzle temperature from Prusa MK3/MK4/XL printers on your local network.',
    badge: 'Local API',
    color: '#ff6b35',
    icon: `<svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M12 8v4l3 3"/></svg>`,
  },
  {
    name: 'Flexible Integrations',
    desc: 'Drop in a JSON config file to add any printer or service. No code changes — the integration engine discovers and applies it at runtime.',
    badge: 'Extensible',
    color: '#ff9f43',
    icon: `<svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2L2 7l10 5 10-5-10-5z"/><path d="M2 17l10 5 10-5"/><path d="M2 12l10 5 10-5"/></svg>`,
  },
  {
    name: 'ESP32 Scales',
    desc: 'Custom firmware for HX711-based load cells. Weighs spools continuously and pushes updates over Wi-Fi.',
    badge: 'Hardware',
    color: '#51cf66',
    icon: `<svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M2 20h20M6 20V10l6-6 6 6v10"/><path d="M10 20v-5h4v5"/></svg>`,
  },
  {
    name: 'Open Filament DB',
    desc: 'Sync material data from the community Open Filament Database — brand names, colors, and print parameters.',
    badge: 'API',
    color: '#9966ff',
    icon: `<svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><ellipse cx="12" cy="5" rx="9" ry="3"/><path d="M21 12c0 1.66-4 3-9 3s-9-1.34-9-3"/><path d="M3 5v14c0 1.66 4 3 9 3s9-1.34 9-3V5"/></svg>`,
  },
  {
    name: 'Web NFC',
    desc: 'Scan spool tags directly from Chrome on Android. No app install required — the browser does the reading.',
    badge: 'Web API',
    color: '#ff6b9d',
    icon: `<svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M6.5 6.5a7 7 0 000 11M17.5 6.5a7 7 0 010 11M3 3a14 14 0 000 18M21 3a14 14 0 010 18"/><circle cx="12" cy="12" r="1.5"/></svg>`,
  },
  {
    name: 'Docker Compose',
    desc: 'The entire stack ships as a single Compose file. Deploy on any Linux host, NAS, or home server.',
    badge: 'Infrastructure',
    color: '#1991e5',
    icon: `<svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="7" width="4" height="4" rx="1"/><rect x="8" y="7" width="4" height="4" rx="1"/><rect x="14" y="7" width="4" height="4" rx="1"/><rect x="2" y="13" width="4" height="4" rx="1"/><rect x="8" y="13" width="4" height="4" rx="1"/><path d="M20 9h2v6a2 2 0 01-2 2H8"/><path d="M14 19l-2 2-2-2"/></svg>`,
  },
  {
    name: 'Kubernetes / Helm',
    desc: 'First-class Helm chart included for production deployments on k3s, k8s, or any compliant cluster.',
    badge: 'Production',
    color: '#326ce5',
    icon: `<svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><polygon points="12 2 22 8.5 22 15.5 12 22 2 15.5 2 8.5 12 2"/><circle cx="12" cy="12" r="3"/></svg>`,
  },
]
</script>

<style scoped>
.integrations-section {
  padding: 80px 0 120px;
}

.section-header {
  margin-bottom: 60px;
}

.integrations-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 16px;
}

.integration-card {
  display: flex;
  align-items: flex-start;
  gap: 16px;
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 22px;
  transition: border-color 0.2s, transform 0.2s, box-shadow 0.2s;
}

.integration-card:hover {
  border-color: rgba(102, 153, 255, 0.25);
  transform: translateY(-2px);
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
}

.integration-icon {
  flex-shrink: 0;
  margin-top: 2px;
}

.integration-info { flex: 1; min-width: 0; }

.integration-name {
  font-size: 15px;
  font-weight: 700;
  color: var(--text);
  margin-bottom: 5px;
  letter-spacing: -0.01em;
}

.integration-desc {
  font-size: 13px;
  line-height: 1.6;
  color: var(--text-muted);
}

.integration-badge {
  flex-shrink: 0;
  font-size: 10px;
  font-weight: 700;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  padding: 4px 9px;
  border-radius: 100px;
  border: 1px solid;
  white-space: nowrap;
  align-self: flex-start;
}

@media (max-width: 760px) {
  .integrations-grid { grid-template-columns: 1fr; }
  .integrations-section { padding: 60px 0 80px; }
}
</style>

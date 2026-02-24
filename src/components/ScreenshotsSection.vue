<template>
  <section class="screenshots-section">
    <div class="container">
      <div class="section-header reveal">
        <p class="section-label">In action</p>
        <h2 class="section-title">See what you're getting</h2>
        <p class="section-subtitle">
          A real deployment, running live — not marketing mock-ups.
        </p>
      </div>

      <div class="tab-bar reveal">
        <button
          v-for="tab in tabs"
          :key="tab.id"
          :class="['tab-btn', { active: active === tab.id }]"
          @click="active = tab.id"
        >
          {{ tab.label }}
        </button>
      </div>

      <div class="screenshot-frame reveal reveal-delay-1">
        <div class="frame-bar">
          <div class="frame-dots"><span></span><span></span><span></span></div>
          <span class="frame-url">spoolsync.local / {{ currentTab.path }}</span>
          <div class="live-chip"><span class="live-dot"></span>Live</div>
        </div>
        <div class="screenshot-wrap">
          <template v-for="tab in tabs" :key="tab.id">
            <picture>
              <source :srcset="tab.img" type="image/webp" />
              <img
                :src="tab.fallback"
                :alt="tab.label"
                :class="['screenshot-img', { visible: active === tab.id }]"
                loading="lazy"
              />
            </picture>
          </template>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from "vue";

const tabs = [
  {
    id: "dashboard",
    label: "Dashboard",
    path: "dashboard",
    img: "/screenshots/dashboard.webp",
    fallback: "/screenshots/dashboard.png",
  },
  {
    id: "spools",
    label: "Filament",
    path: "spools",
    img: "/screenshots/spools.webp",
    fallback: "/screenshots/spools.png",
  },
  {
    id: "inventory",
    label: "Inventory",
    path: "inventory",
    img: "/screenshots/inventory.webp",
    fallback: "/screenshots/inventory.png",
  },
  {
    id: "storage",
    label: "Storage",
    path: "storage",
    img: "/screenshots/storage.webp",
    fallback: "/screenshots/storage.png",
  },
  {
    id: "printers",
    label: "Printers",
    path: "printers",
    img: "/screenshots/printers.webp",
    fallback: "/screenshots/printers.png",
  },
  {
    id: "scales",
    label: "Scales",
    path: "spool-holders",
    img: "/screenshots/scales.webp",
    fallback: "/screenshots/scales.png",
  },
  {
    id: "orders",
    label: "Orders",
    path: "orders",
    img: "/screenshots/orders.webp",
    fallback: "/screenshots/orders.png",
  },
  {
    id: "esp32",
    label: "ESP32",
    path: "esp32-devices",
    img: "/screenshots/esp32.webp",
    fallback: "/screenshots/esp32.png",
  },
  {
    id: "weigh",
    label: "Weigh",
    path: "weigh",
    img: "/screenshots/weigh.webp",
    fallback: "/screenshots/weigh.png",
  },
  {
    id: "settings",
    label: "Settings",
    path: "settings",
    img: "/screenshots/settings.webp",
    fallback: "/screenshots/settings.png",
  },
];

const active = ref("dashboard");
const currentTab = computed(() => tabs.find((t) => t.id === active.value));
</script>

<style scoped>
.screenshots-section {
  padding: 80px 0 120px;
}

.section-header {
  margin-bottom: 48px;
}

.tab-bar {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
  margin-bottom: 20px;
}

.tab-btn {
  padding: 8px 18px;
  border-radius: 100px;
  border: 1px solid var(--border);
  background: transparent;
  color: var(--text-muted);
  font-size: 13px;
  font-weight: 500;
  font-family: inherit;
  cursor: pointer;
  transition: all 0.2s;
}

.tab-btn:hover {
  border-color: var(--primary);
  color: var(--text);
}

.tab-btn.active {
  background: var(--primary-dim);
  border-color: rgba(102, 153, 255, 0.4);
  color: var(--primary);
}

.screenshot-frame {
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  overflow: hidden;
  box-shadow:
    0 0 0 1px rgba(102, 153, 255, 0.06),
    0 32px 80px rgba(0, 0, 0, 0.5);
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
  font-family: "JetBrains Mono", monospace;
  flex: 1;
}

.live-chip {
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
}

.screenshot-wrap {
  position: relative;
  background: var(--card);
  /* fixed height so layout doesn't shift between tabs */
  aspect-ratio: 1280 / 800;
}

.screenshot-img {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: top left;
  opacity: 0;
  transition: opacity 0.3s ease;
  display: block;
}

.screenshot-img.visible {
  opacity: 1;
}
</style>

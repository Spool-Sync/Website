<template>
  <div class="spool-row">
    <div class="swatch" :style="{ background: color }"></div>
    <div class="spool-info">
      <div class="spool-name">{{ brand }} <span>{{ name }}</span></div>
      <div class="spool-bar">
        <div class="bar-track">
          <div class="bar-fill" :style="{ width: pct + '%', background: warn ? '#ffd43b' : color }"></div>
        </div>
        <span :class="['spool-weight', { warn }]">{{ weight }}g</span>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  color:  { type: String, required: true },
  brand:  { type: String, required: true },
  name:   { type: String, required: true },
  weight: { type: [String, Number], required: true },
  max:    { type: [String, Number], default: 1000 },
  warn:   { type: Boolean, default: false },
})

const pct = computed(() => Math.round((+props.weight / +props.max) * 100))
</script>

<style scoped>
.spool-row {
  display: flex;
  align-items: center;
  gap: 10px;
  background: var(--surface);
  border: 1px solid var(--border-dim);
  border-radius: var(--radius-sm);
  padding: 10px 12px;
}

.swatch {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  flex-shrink: 0;
}

.spool-info { flex: 1; min-width: 0; }

.spool-name {
  font-size: 11px;
  font-weight: 600;
  color: var(--text-muted);
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  margin-bottom: 5px;
}

.spool-name span { color: var(--text); }

.spool-bar {
  display: flex;
  align-items: center;
  gap: 8px;
}

.bar-track {
  flex: 1;
  height: 4px;
  background: var(--border);
  border-radius: 2px;
  overflow: hidden;
}

.bar-fill {
  height: 100%;
  border-radius: 2px;
  transition: width 0.4s ease;
}

.spool-weight {
  font-size: 11px;
  font-weight: 600;
  color: var(--text-muted);
  font-family: 'JetBrains Mono', monospace;
  white-space: nowrap;
}

.spool-weight.warn { color: #ffd43b; }
</style>

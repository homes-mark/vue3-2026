<script setup>
import { computed, ref } from 'vue'

const presets = [
  { id: 'sky-blue', name: '天空蓝', red: 58, green: 135, blue: 240 },
  { id: 'coral', name: '珊瑚橙', red: 255, green: 111, blue: 97 },
  { id: 'mint', name: '薄荷绿', red: 45, green: 212, blue: 149 },
  { id: 'amber', name: '琥珀黄', red: 255, green: 191, blue: 0 },
]

const initialColor = presets[0]
const red = ref(initialColor.red)
const green = ref(initialColor.green)
const blue = ref(initialColor.blue)

// 色块和文本共用这一个计算结果，不需要另外保存颜色。
const rgbColor = computed(() => `rgb(${red.value}, ${green.value}, ${blue.value})`)

function applyPreset(preset) {
  red.value = preset.red
  green.value = preset.green
  blue.value = preset.blue
}
</script>

<template>
  <main class="palette">
    <header class="page-header">
      <p class="section-label">Vue 3 案例练习</p>
      <h1>RGB 调色盘</h1>
      <p>拖动滑块混合红、绿、蓝。每个通道的取值范围是 0–255。</p>
    </header>

    <div class="panels">
      <section class="panel" aria-labelledby="channels-heading">
        <h2 id="channels-heading">调节通道</h2>

        <div class="channel channel-red">
          <div class="channel-heading">
            <label for="red">红色 R</label>
            <span>{{ red }}</span>
          </div>
          <input id="red" v-model.number="red" type="range" min="0" max="255" step="1" />
        </div>

        <div class="channel channel-green">
          <div class="channel-heading">
            <label for="green">绿色 G</label>
            <span>{{ green }}</span>
          </div>
          <input id="green" v-model.number="green" type="range" min="0" max="255" step="1" />
        </div>

        <div class="channel channel-blue">
          <div class="channel-heading">
            <label for="blue">蓝色 B</label>
            <span>{{ blue }}</span>
          </div>
          <input id="blue" v-model.number="blue" type="range" min="0" max="255" step="1" />
        </div>

        <div class="presets">
          <h3>预设颜色</h3>
          <div class="preset-list">
            <button
              v-for="preset in presets"
              :key="preset.id"
              type="button"
              @click="applyPreset(preset)"
            >
              {{ preset.name }}
            </button>
          </div>
        </div>
      </section>

      <section class="panel preview" aria-labelledby="preview-heading">
        <h2 id="preview-heading">实时预览</h2>
        <div class="swatch" :style="{ backgroundColor: rgbColor }" aria-hidden="true"></div>
        <output class="color-value" for="red green blue">{{ rgbColor }}</output>
      </section>
    </div>
  </main>
</template>

<style scoped>
.palette {
  max-width: 60rem;
  margin: 0 auto;
  padding: clamp(1.25rem, 6vw, 4.5rem) clamp(1rem, 4vw, 2rem) 2.5rem;
}

.page-header {
  margin-bottom: 2rem;
}

.page-header p {
  margin: 0;
  color: #aab8cc;
}

.page-header .section-label {
  color: #94caff;
  font-size: 0.875rem;
  font-weight: 650;
  letter-spacing: 0.08em;
}

h1 {
  margin: 0.4rem 0;
  font-size: clamp(2rem, 5vw, 3.5rem);
  line-height: 1.2;
}

.panels {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 1rem;
}

.panel {
  padding: clamp(1rem, 3vw, 1.5rem);
  border: 1px solid #344159;
  border-radius: 1rem;
  background: #172235;
}

h2 {
  margin: 0 0 1rem;
  font-size: 1.25rem;
}

.channel {
  margin-top: 0.85rem;
}

.channel-heading {
  display: flex;
  justify-content: space-between;
  gap: 1rem;
}

.channel-heading span {
  color: #c3cfe0;
  font-variant-numeric: tabular-nums;
}

.channel input {
  display: block;
  width: 100%;
  min-height: 1.75rem;
  margin: 0.25rem 0 0;
  cursor: pointer;
}

.channel-red input { accent-color: #ff808a; }
.channel-green input { accent-color: #57e1a5; }
.channel-blue input { accent-color: #7abaff; }

.presets {
  margin-top: 1.25rem;
  padding-top: 1rem;
  border-top: 1px solid #344159;
}

.presets h3 {
  margin: 0 0 0.6rem;
  font-size: 1rem;
}

.preset-list {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.preset-list button {
  min-height: 2.5rem;
  padding: 0.35rem 0.75rem;
  border: 1px solid #53627a;
  border-radius: 0.5rem;
  color: inherit;
  background: #22314a;
  cursor: pointer;
}

.preset-list button:hover {
  background: #324565;
}

.channel input:focus-visible,
.preset-list button:focus-visible {
  outline: 2px solid #94caff;
  outline-offset: 3px;
}

.preview {
  display: flex;
  flex-direction: column;
}

.swatch {
  flex: 1;
  min-height: 12rem;
  border: 1px solid #53627a;
  border-radius: 0.75rem;
}

.color-value {
  margin-top: 0.85rem;
  color: #e5edf9;
  font-family: ui-monospace, Consolas, monospace;
  text-align: center;
  overflow-wrap: anywhere;
}

@media (max-width: 42rem) {
  .panels {
    grid-template-columns: 1fr;
  }
}
</style>

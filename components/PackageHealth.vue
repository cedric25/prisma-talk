<template>
  <a
    :href="snykLink"
    target="_blank"
    class="block p-1 rounded hover:bg-gray-100"
    style="border-bottom-width: 0"
  >
    <div class="package-health">
      <div class="package-health-score text-xs">
        <div class="vue--layout-space-between">
          <span class="number">{{ score }} / 100</span>
        </div>
      </div>
      <div class="package-health-bar">
        <div class="score-bar">
          <div class="bar">
            <div
              class="value"
              :class="scoreColor"
              :style="`width: ${score}%`"
            ></div>
          </div>
        </div>
      </div>
    </div>
  </a>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'

const props = defineProps({
  score: { default: 0 },
  snykLink: { default: '' },
})

const score = ref(props.score)

const scoreColor = computed(() => {
  return score.value >= 85 ? 'green' : 'orange'
})
</script>

<style scoped>
.bar {
  position: relative;
  width: 100%;
  height: 0.5rem;
  background: #ebeaea;
}
.bar .value {
  position: absolute;
  top: 0;
  left: 0;
  height: 0.5rem;
}
.bar .value.green {
  background: #52baa6;
}
.bar .value.orange {
  background-color: #d38a3b;
}
</style>

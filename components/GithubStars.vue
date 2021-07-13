<template>
  <div class="github-stars-wrap flex">
    <div class="btn btn-sm btn-with-count flex items-center">
      <svg
        aria-hidden="true"
        viewBox="0 0 16 16"
        version="1.1"
        data-view-component="true"
        height="16"
        width="16"
        class="octicon octicon-star mr-1"
      >
        <path
          fill-rule="evenodd"
          d="M8 .25a.75.75 0 01.673.418l1.882 3.815 4.21.612a.75.75 0 01.416 1.279l-3.046 2.97.719 4.192a.75.75 0 01-1.088.791L8 12.347l-3.766 1.98a.75.75 0 01-1.088-.79l.72-4.194L.818 6.374a.75.75 0 01.416-1.28l4.21-.611L7.327.668A.75.75 0 018 .25zm0 2.445L6.615 5.5a.75.75 0 01-.564.41l-3.097.45 2.24 2.184a.75.75 0 01.216.664l-.528 3.084 2.769-1.456a.75.75 0 01.698 0l2.77 1.456-.53-3.084a.75.75 0 01.216-.664l2.24-2.183-3.096-.45a.75.75 0 01-.564-.41L8 2.694v.001z"
        ></path>
      </svg>
      <span class="ml-1"> Star </span>
    </div>
    <div class="social-count flex items-center">{{ counter }}</div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const props = defineProps({
  count: {
    default: 0,
  },
})

const counter = ref(props.count)
</script>

<style>
:root {
  --color-btn-bg: #fafbfc;
  --color-btn-border: rgba(27, 31, 35, 0.15);
  --color-btn-shadow: 0 1px 0 rgba(27, 31, 35, 0.04);
  --color-btn-inset-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.25);
  --color-btn-text: #24292e;

  --color-social-count-bg: #fff;
  --color-shadow-small: 0 1px 0 rgba(27, 31, 35, 0.04);
  --color-shadow-highlight: inset 0 1px 0 rgba(255, 255, 255, 0.25);
  --color-text-primary: #24292e;

  --color-text-tertiary: #6a737d;

  --height: 26px;
}

.github-stars-wrap {
  font-family: 'Roboto Light', sans-serif;
}

.btn {
  height: var(--height);

  background-color: var(--color-btn-bg);
  border-color: var(--color-btn-border) !important;
  box-shadow: var(--color-btn-shadow), var(--color-btn-inset-shadow);
  color: var(--color-btn-text);
  transition: 0.2s cubic-bezier(0.3, 0, 0.5, 1);
  transition-property: color, background-color, border-color;

  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  border: 1px solid;
  border-radius: 6px;
  font-size: 14px;
  font-weight: 500;
  line-height: 20px;
  padding: 5px 16px;
  position: relative;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  vertical-align: middle;
  white-space: nowrap;
}
.btn-sm {
  font-size: 12px;
  line-height: 20px;
  padding: 3px 12px;
}
.btn-with-count {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}

.social-count {
  height: var(--height);

  background-color: var(--color-social-count-bg);
  border: 1px solid var(--color-btn-border);
  border-bottom-right-radius: 6px;
  border-left: 0;
  border-top-right-radius: 6px;
  box-shadow: var(--color-shadow-small), var(--color-shadow-highlight);
  color: var(--color-text-primary);
  font-size: 12px;
  line-height: 20px;
  padding: 3px 12px;
  position: relative;
  vertical-align: middle;
}

.btn-sm .octicon {
  vertical-align: text-top;
}

.btn .octicon {
  fill: var(--color-text-tertiary);
}
</style>

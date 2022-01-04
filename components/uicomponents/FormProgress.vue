<template>
  <progress class="form-progress" :value="progress" max="100"></progress>
</template>

<script>
export default {
  props: {
    progress: {
      type: Number,
      default: 0,
      required: true,
    },
  },
};
</script>

<style>
progress {
  border-radius: 1px;
  width: 100%;
  height: 6px;
  background: #f5f5f5;
}
progress::-webkit-progress-bar {
  background-color: #f5f5f5;
}
progress::-webkit-progress-value {
  background-color: var(--brand-blue);
  transition: 0.3s all linear;
}
progress::-moz-progress-bar {
  background: var(--brand-blue);
}
</style>

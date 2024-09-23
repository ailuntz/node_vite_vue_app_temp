<script setup lang="ts">
import { onMounted, onUnmounted } from 'vue';
import lottie from 'lottie-web';

const props = defineProps({
  onEnd: Function,
});

const containerId = 'lottie-container';

onMounted(() => {
  const container = document.getElementById(containerId);
  if (container) {
    lottie.loadAnimation({
      container: container,
      renderer: 'svg',
      loop: true,
      autoplay: true,
      path: `${import.meta.env.BASE_URL}data.json`, 
    });
  }

  const timer = setTimeout(() => {
    if (props.onEnd) props.onEnd();
    lottie.destroy();
  }, 2000);

  onUnmounted(() => {
    clearTimeout(timer);
    lottie.destroy();
  });
});
</script>

<template>
  <div
    :id="containerId"
    style="width: 100vw; height: 100vh; position: fixed; top: 0; left: 0; z-index: 9999; background-color: rgba(0, 0, 0, 0.5); backdrop-filter: blur(10px); display: flex; justify-content: center; align-items: center;"
  ></div>
</template>

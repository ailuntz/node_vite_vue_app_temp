<!-- VideoBackground.vue -->
<template>
    <div class="video-bg">
      <video ref="videoRef" width="320" height="240" autoplay muted loop>
        <source src="https://assets.codepen.io/3364143/7btrrd.mp4" type="video/mp4" />
        Your browser does not support the video tag.
      </video>
    </div>
  </template>
  
  <script setup lang="ts">
  import { ref, onMounted, onBeforeUnmount } from 'vue';
  
  // 通过 ref 访问 DOM 元素
  const videoRef = ref<HTMLVideoElement | null>(null);
  
  onMounted(() => {
    const video = videoRef.value;
    if (video) {
      // 在视频结束时确保无缝循环播放
      video.addEventListener('ended', () => {
        video.currentTime = 0.5;
        video.play();
      });
    }
  });
  
  onBeforeUnmount(() => {
    const video = videoRef.value;
    if (video) {
      video.removeEventListener('ended', () => {}); // 清理事件监听器
    }
  });
  </script>
  
  <style scoped>
  .video-bg {
    position: fixed;
    right: 0;
    top: 0;
    width: 100%;
    height: 100%;
    /* z-index: -1; */
  }
  
  .video-bg video {
    width: 100%;
    height: 100%;
    -o-object-fit: cover;
       object-fit: cover;
  }
  </style>
  
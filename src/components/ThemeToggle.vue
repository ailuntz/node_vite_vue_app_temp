<script setup lang="ts">
import { ref, watchEffect } from 'vue';

// 使用 ref 创建响应式的状态
const isLightMode = ref(false);

// 切换模式的逻辑
const handleToggle = () => {
  isLightMode.value = !isLightMode.value;
};

// 使用 watchEffect 来监听 isLightMode 的变化，并更新 body 的 class
watchEffect(() => {
  if (isLightMode.value) {
    document.body.classList.add('light-mode');
  } else {
    document.body.classList.remove('light-mode');
  }
});
</script>

<template>
  <div class="dark-light" @click="handleToggle" style="cursor: pointer">
    <svg
      viewBox="0 0 24 24"
      stroke="currentColor"
      stroke-width="1.5"
      fill="none"
      stroke-linecap="round"
      stroke-linejoin="round"
      style="width: 24px; height: 24px"
    >
      <path d="M21 12.79A9 9 0 1111.21 3 7 7 0 0021 12.79z" />
    </svg>
  </div>
</template>

<style >
/* 定义不同模式下的样式 */
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@200;300;400;500;600;700&display=swap");
* {
  outline: none;
  box-sizing: border-box;
}


html {
  box-sizing: border-box;
  -webkit-font-smoothing: antialiased;
}

body {
  font-family: var(--body-font);
  background-image: url(https://wallpapershome.com/images/wallpapers/macos-big-sur-1280x720-dark-wwdc-2020-22655.jpg);
  background-size: cover;
  background-position: center;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  padding: 2em;
  width: 100%;
  height: 100vh;
}
@media screen and (max-width: 480px) {
  body {
    padding: 0.8em;
  }
}

:root {
  --theme-bg-color: rgba(16 18 27 / 40%);
  --border-color: rgba(113 119 144 / 25%);
  --theme-color: #999ba5;
  --inactive-color: rgb(113 119 144 / 78%);
  --body-font: "Poppins", sans-serif;
  --hover-menu-bg: rgba(12 15 25 / 30%);
  --content-title-color: #999ba5;
  --content-bg: rgb(146 151 179 / 13%);
  --button-inactive: rgb(249 250 251 / 55%);
  --dropdown-bg: #21242d;
  --dropdown-hover: rgb(42 46 60);
  --popup-bg: rgb(22 25 37);
  --search-bg: #14162b;
  --overlay-bg: rgba(236, 39, 59, 0.3);
  --scrollbar-bg: rgb(1 2 3 / 40%);
}

.app {
  background-color: var(--theme-bg-color);
  max-width: 1250px;
  max-height: 860px;
  height: 90vh;
  display: flex;
  flex-direction: column;
  overflow: hidden;
  position: relative;
  width: 100%;
  border-radius: 14px;
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  font-size: 15px;
  font-weight: 500;
}

.light-mode {
  --theme-bg-color: rgb(255 255 255 / 31%);
  --theme-color: #3c3a3a;
  --inactive-color: #333333;
  --button-inactive: #3c3a3a;
  --search-bg: rgb(255 255 255 / 31%);
  --dropdown-bg: #f7f7f7;
  --overlay-bg: rgb(255 255 255 / 30%);
  --dropdown-hover: rgb(236 236 236);
  --border-color: rgb(255 255 255 / 35%);
  --popup-bg: rgb(255 255 255);
  --hover-menu-bg: rgba(255 255 255 / 35%);
  --scrollbar-bg: rgb(255 253 253 / 57%);
  --content-title-color: --theme-color;
}


img {
  max-width: 100%;
}

.dark-light {
  position: fixed;
  bottom: 50px;
  right: 30px;
  background-color: var(--dropdown-bg);
  box-shadow: -1px 3px 8px -1px rgba(0, 0, 0, 0.2);
  padding: 8px;
  border-radius: 50%;
  z-index: 3;
  cursor: pointer;
}
.dark-light svg {
  width: 24px;
  flex-shrink: 0;
  fill: #ffce45;
  stroke: #ffce45;
  transition: 0.5s;
}

.light-mode .dark-light svg {
  fill: transparent;
  stroke: var(--theme-color);
}
.light-mode .profile-img {
  border: 2px solid var(--theme-bg-color);
}
.light-mode .content-section ul {
  background-color: var(--theme-bg-color);
}
.light-mode .pop-up__title {
  border-color: var(--theme-color);
}
.light-mode .dropdown.is-active ul {
  background-color: rgba(255, 255, 255, 0.94);
}

body.light-mode:before,
body.light-mode .video-bg:before {
  content: "";
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100vh;
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.72) 0%, rgba(255, 255, 255, 0.45) 100%);
  -webkit-backdrop-filter: saturate(3);
          backdrop-filter: saturate(3);
}
</style>

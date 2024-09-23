<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount } from 'vue';

const handlemainMenuClick = (event: Event) => {
  const mainHeaderLinks = document.querySelectorAll('.main-header-link');
  mainHeaderLinks.forEach((mainHeaderLink) => {
    mainHeaderLink.classList.remove('is-active');
  });
  (event.target as HTMLElement).classList.add('is-active');
};

// 挂载时添加事件监听，卸载时移除
onMounted(() => {
  const mainHeaderLinks = document.querySelectorAll('.main-header-link');
  mainHeaderLinks.forEach((mainHeaderLink) => {
    mainHeaderLink.addEventListener('click', handlemainMenuClick);
  });
});

onBeforeUnmount(() => {
  const mainHeaderLinks = document.querySelectorAll('.main-header-link');
  mainHeaderLinks.forEach((mainHeaderLink) => {
    mainHeaderLink.removeEventListener('click', handlemainMenuClick);
  });
});
</script>

<template>
  <div className="main-header">
    <a className="menu-link-main" href="#">All Apps</a>
    <div className="header-menu">
    <a className="main-header-link is-active" href="#">Desktop</a>
    <a className="main-header-link" href="#">Mobile</a>
    <a className="main-header-link" href="#">Web</a>
    </div>
  </div>
</template>

<style scoped>
.main-header {
  display: flex;
  align-items: center;
  border-bottom: 1px solid var(--border-color);
  height: 58px;
  flex-shrink: 0;
}
.main-header .header-menu {
  margin-left: 150px;
}
@media screen and (max-width: 1055px) {
  .main-header .header-menu {
    margin: auto;
  }
}
.main-header .header-menu a {
  padding: 20px 24px;
}

.menu-link-main {
  text-decoration: none;
  color: var(--theme-color);
  padding: 0 30px;
}
@media screen and (max-width: 1055px) {
  .menu-link-main {
    display: none;
  }
}

.header-menu {
  display: flex;
  align-items: center;
}

.header-menu a {
  padding: 20px 30px;
  text-decoration: none;
  color: var(--inactive-color);
  border-bottom: 2px solid transparent;
  transition: 0.3s;
}

.header-menu a.is-active,
.header-menu a:hover {
  color: var(--theme-color);
  border-bottom: 2px solid var(--theme-color);
}
</style>

<template>
  <button
    class="dropdown"
    :class="{ 'is-active': isActive }"
    @click="toggleDropdown"
  >
    <ul>
      <li><a href="#">Go to Discover</a></li>
      <li><a href="#">Learn more</a></li>
      <li><a href="#">Uninstall</a></li>
    </ul>
  </button>
</template>

<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount } from 'vue';

const isActive = ref(false);

const toggleDropdown = (e: Event) => {
  e.stopPropagation();
  isActive.value = !isActive.value;
};

const handleClickOutside = () => {
  isActive.value = false;
};

onMounted(() => {
  document.addEventListener('click', handleClickOutside);
});

onBeforeUnmount(() => {
  document.removeEventListener('click', handleClickOutside);
});
</script>

<style scoped>
.dropdown {
  position: relative;
  height: 53px;
  width: 40px;
  top: -24px;
  display: flex;
  left: -5px;
  background: transparent;
  border: none;
  cursor: pointer;
}

.dropdown ul {
  position: absolute;
  background: var(--dropdown-bg);
  height: 110px;
  width: 120px;
  right: 0;
  top: 20px;
  pointer-events: none;
  opacity: 0;
  transform: translatey(10px);
  transition: all 0.4s ease;
}

.dropdown ul li a {
  text-decoration: none;
  color: var(--theme-color);
  font-size: 12px;
}

.dropdown.is-active ul {
  opacity: 1;
  pointer-events: all;
  transform: translatey(25px);
}

.dropdown.is-active ul li:hover {
  background-color: var(--dropdown-hover);
}
</style>

  
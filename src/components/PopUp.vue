<!-- Popup.vue -->
<template>
  <!-- <teleport to="body"> -->
    <div v-if="isVisible" className="pop-up">
              <div className="pop-up__title">Update This App
                <svg className="close feather feather-x-circle" width="24" height="24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round">
                <circle cx="12" cy="12" r="10" />
                <path d="M15 9l-6 6M9 9l6 6" />
                </svg>
              </div>
              <div className="pop-up__subtitle">Adjust your selections for advanced options as desired before continuing. <a href="#">Learn more</a></div>
              <div className="checkbox-wrapper">
                <input type="checkbox" id="check1" className="checkbox" />
                <label htmlFor="check1">Import previous settings and preferences</label>
              </div>
              <div className="checkbox-wrapper">
                <input type="checkbox" id="check2" className="checkbox" />
                <label htmlFor="check2">Remove old versions</label>
              </div>
              <div className="content-button-wrapper">
                <button className="content-button status-button open close" @click="closePopup" >Cancel</button>
                <button className="content-button status-button">Continue</button>
              </div>
              </div>
  <!-- </teleport> -->
</template>

<script setup lang="ts">

import { ref } from 'vue';

// 内部控制弹窗的可见性
const isVisible = ref(false);

const openPopup = () => {
  isVisible.value = true;
};

const closePopup = () => {
  isVisible.value = false;
};

// 将方法提供给父组件
defineExpose({
  openPopup,
  closePopup,
});

</script>

<style scoped>
.pop-up {
  position: absolute;
  padding: 30px 40px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  overflow-y: auto;
  box-shadow: 0px 6px 30px rgba(0, 0, 0, 0.4);
  transition: all 0.3s;
  z-index: 10;
  background-color: var(--popup-bg);
  width: 500px;
  /* visibility: hidden;
  opacity: 0; */
  border-radius: 6px;
  display: flex;
  flex-direction: column;
  white-space: normal;
}

@media screen and (max-width: 570px) {
  .pop-up {
    width: 100%;
  }
}

.pop-up.visible {
  visibility: visible;
  opacity: 1;
}

.pop-up__title {
  padding-bottom: 20px;
  border-bottom: 1px solid var(--border-color);
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.pop-up__subtitle {
  white-space: normal;
  margin: 20px 0;
  font-size: 14px;
  font-weight: 400;
  line-height: 1.8em;
}

.pop-up__subtitle a {
  color: var(--theme-color);
}

.checkbox-wrapper {
  margin-bottom: 15px;
}

.content-button-wrapper {
  display: flex;
  justify-content: space-between;
}

.overlay-app.is-active {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
  z-index: 5;
}

.status-button {
  margin-top: 20px;
  padding: 10px 20px;
  cursor: pointer;
}
</style>

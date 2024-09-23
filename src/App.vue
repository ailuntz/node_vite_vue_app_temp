<script setup lang="ts">
import { ref } from 'vue';
import LoadingAnimation from './components/LoadingAnimation.vue';
import VideoBackground from './components/VideoBackground.vue';
import AppHeader from './components/AppHeader.vue';
import AppLeftside from './components/AppLeftside.vue';
import AppMainHeader from './components/AppMainHeader.vue';
import PopUp from './components/PopUp.vue';
import ThemeToggle from './components/ThemeToggle.vue';
import DropdownMenu from './components/DropdownMenu.vue';
import HelloWorld from './components/HelloWorld.vue';
import { RouterLink, RouterView } from 'vue-router';

const showAnimation = ref(true);

const handleAnimationEnd = () => {
  showAnimation.value = false;
};

// 通过 ref 引用弹窗组件实例
const popupRef = ref();

// 打开弹窗
const openPopUp = () => {
  console.log(popupRef.value.openPopup);
  popupRef.value?.openPopup(); // 调用 Popup 组件内的方法
};

</script>

<template>
  <div v-if="showAnimation">
    <LoadingAnimation :onEnd="handleAnimationEnd" />
  </div>

  <div v-else>
    <VideoBackground /> <!-- 引入视频背景组件 -->
    <ThemeToggle />
    <div className="app">     
      <AppHeader />
        <div className="wrapper">
          <AppLeftside />
          <div className="main-container">
            <AppMainHeader />
          <div className="content-wrapper">
            <div className="content-wrapper-header">
            <div className="content-wrapper-context">
              <h3 className="img-content">
              <svg viewBox="0 0 512 512">
                <path d="M467 0H45C20.099 0 0 20.099 0 45v422c0 24.901 20.099 45 45 45h422c24.901 0 45-20.099 45-45V45c0-24.901-20.099-45-45-45z" fill="#d6355b" data-original="#ff468c" />
                <path xmlns="http://www.w3.org/2000/svg" d="M512 45v422c0 24.901-20.099 45-45 45H256V0h211c24.901 0 45 20.099 45 45z" fill="#d6355b" data-original="#d72878" />
                <path xmlns="http://www.w3.org/2000/svg" d="M467 30H45c-8.401 0-15 6.599-15 15v422c0 8.401 6.599 15 15 15h422c8.401 0 15-6.599 15-15V45c0-8.401-6.599-15-15-15z" fill="#2e000a" data-original="#700029" />
                <path xmlns="http://www.w3.org/2000/svg" d="M482 45v422c0 8.401-6.599 15-15 15H256V30h211c8.401 0 15 6.599 15 15z" fill="#2e000a" data-original="#4d0e06" />
                <path xmlns="http://www.w3.org/2000/svg" d="M181 391c-41.353 0-75-33.647-75-75 0-8.291 6.709-15 15-15s15 6.709 15 15c0 24.814 20.186 45 45 45s45-20.186 45-45-20.186-45-45-45c-41.353 0-75-33.647-75-75s33.647-75 75-75 75 33.647 75 75c0 8.291-6.709 15-15 15s-15-6.709-15-15c0-24.814-20.186-45-45-45s-45 20.186-45 45 20.186 45 45 45c41.353 0 75 33.647 75 75s-33.647 75-75 75z" fill="#d6355b" data-original="#ff468c" />
                <path xmlns="http://www.w3.org/2000/svg" d="M391 361h-30c-8.276 0-15-6.724-15-15V211h45c8.291 0 15-6.709 15-15s-6.709-15-15-15h-45v-45c0-8.291-6.709-15-15-15s-15 6.709-15 15v45h-15c-8.291 0-15 6.709-15 15s6.709 15 15 15h15v135c0 24.814 20.186 45 45 45h30c8.291 0 15-6.709 15-15s-6.709-15-15-15z" fill="#d6355b" data-original="#d72878" />
              </svg>
              Adobe Stock
              </h3>
              <div className="content-text">Grab yourself 10 free images from Adobe Stock in a 30-day free trial plan and find perfect image, that will help you with your new project.</div>
              <button className="content-button">Start free trial</button>
            </div>
            <img className="content-wrapper-img" src="https://assets.codepen.io/3364143/glass.png" alt="" />
            </div>
            <div className="content-section">
              <div className="content-section-title">Installed</div>
              <ul>
                  <li className="adobe-product">
                  <div class="products">
                    <svg viewBox="0 0 52 52" :style="{ border: '1px solid #3291b8' }" xmlns="http://www.w3.org/2000/svg">
                      <g>
                        <path
                          d="M40.824 52H11.176C5.003 52 0 46.997 0 40.824V11.176C0 5.003 5.003 0 11.176 0h29.649C46.997 0 52 5.003 52 11.176v29.649C52 46.997 46.997 52 40.824 52z"
                          fill="#061e26"
                        />
                        <path
                          d="M12.16 39H9.28V11h9.64c2.613 0 4.553.813 5.82 2.44 1.266 1.626 1.9 3.76 1.9 6.399 0 .934-.027 1.74-.08 2.42-.054.681-.22 1.534-.5 2.561-.28 1.026-.66 1.866-1.14 2.52-.48.654-1.213 1.227-2.2 1.72-.987.494-2.16.74-3.52.74h-7.04V39zm0-12h6.68c.96 0 1.773-.187 2.44-.56.666-.374 1.153-.773 1.46-1.2.306-.427.546-1.04.72-1.84.173-.801.267-1.4.28-1.801.013-.399.02-.973.02-1.72 0-4.053-1.694-6.08-5.08-6.08h-6.52V27zM29.48 33.92l2.8-.12c.106.987.6 1.754 1.48 2.3.88.547 1.893.82 3.04.82s2.14-.26 2.98-.78c.84-.52 1.26-1.266 1.26-2.239s-.36-1.747-1.08-2.32c-.72-.573-1.6-1.026-2.64-1.36-1.04-.333-2.086-.686-3.14-1.06a7.36 7.36 0 01-2.78-1.76c-.987-.934-1.48-2.073-1.48-3.42s.54-2.601 1.62-3.761 2.833-1.739 5.26-1.739c.854 0 1.653.1 2.4.3.746.2 1.28.394 1.6.58l.48.279-.92 2.521c-.854-.666-1.974-1-3.36-1-1.387 0-2.42.26-3.1.78-.68.52-1.02 1.18-1.02 1.979 0 .88.426 1.574 1.28 2.08.853.507 1.813.934 2.88 1.28 1.066.347 2.126.733 3.18 1.16 1.053.427 1.946 1.094 2.68 2s1.1 2.106 1.1 3.6c0 1.494-.6 2.794-1.8 3.9-1.2 1.106-2.954 1.66-5.26 1.66-2.307 0-4.114-.547-5.42-1.64-1.307-1.093-1.987-2.44-2.04-4.04z"
                          fill="#c1dbe6"
                        />
                      </g>
                    </svg>
                    <span>Photoshop</span> <!-- 将文本包裹在 span 中 -->
                  </div>
                  <span className="status">
                    <span className="status-circle green"></span>
                    Updated</span>
                  <div className="button-wrapper">
                    <button className="content-button status-button open">Open</button>
                    <div className="menu">
                      <DropdownMenu />
                    </div>
                  </div>
                  </li>
                  <li className="adobe-product">
                  <div className="products">
                    <svg viewBox="0 0 52 52" :style="{ border: '1px solid #b65a0b' }">
                    <g xmlns="http://www.w3.org/2000/svg">
                      <path d="M40.824 52H11.176C5.003 52 0 46.997 0 40.824V11.176C0 5.003 5.003 0 11.176 0h29.649C46.997 0 52 5.003 52 11.176v29.649C52 46.997 46.997 52 40.824 52z" fill="#261400" data-original="#6d4c13" />
                      <path d="M30.68 39h-3.24l-2.76-9.04h-8.32L13.72 39H10.6l8.24-28h3.32l8.52 28zm-6.72-12l-3.48-11.36L17.12 27h6.84zM37.479 12.24c0 .453-.16.84-.48 1.16-.32.319-.7.479-1.14.479-.44 0-.827-.166-1.16-.5-.334-.333-.5-.713-.5-1.14s.166-.807.5-1.141c.333-.333.72-.5 1.16-.5.44 0 .82.16 1.14.48.321.322.48.709.48 1.162zM37.24 39h-2.88V18.96h2.88V39z" fill="#e6d2c0" data-original="#ffbd2e" />
                    </g>
                    </svg>
                    Illustrator
                  </div>
                  <span className="status">
                    <span className="status-circle"></span>
                    Update Available</span>
                  <div className="button-wrapper">
                    <button className="content-button status-button " @click="openPopUp">Update this app</button>
                    <PopUp ref="popupRef"/>
                    <div className="menu">
                      <DropdownMenu />
                    </div>
                  </div>
                  </li>
                  <li className="adobe-product">
                  <div className="products">
                    <svg viewBox="0 0 52 52" :style="{ border: '1px solid #C75DEB' }">
                    <g xmlns="http://www.w3.org/2000/svg">
                      <path d="M40.824 52H11.176C5.003 52 0 46.997 0 40.824V11.176C0 5.003 5.003 0 11.176 0h29.649C46.997 0 52 5.003 52 11.176v29.649C52 46.997 46.997 52 40.824 52z" fill="#3a3375" data-original="#3a3375" />
                      <path d="M27.44 39H24.2l-2.76-9.04h-8.32L10.48 39H7.36l8.24-28h3.32l8.52 28zm-6.72-12l-3.48-11.36L13.88 27h6.84zM31.48 33.48c0 2.267 1.333 3.399 4 3.399 1.653 0 3.466-.546 5.44-1.64L42 37.6c-2.054 1.254-4.2 1.881-6.44 1.881-4.64 0-6.96-1.946-6.96-5.841v-8.2c0-2.16.673-3.841 2.02-5.04 1.346-1.2 3.126-1.801 5.34-1.801s3.94.594 5.18 1.78c1.24 1.187 1.86 2.834 1.86 4.94V30.8l-11.52.6v2.08zm8.6-5.24v-3.08c0-1.413-.44-2.42-1.32-3.021-.88-.6-1.907-.899-3.08-.899-1.174 0-2.167.359-2.98 1.08-.814.72-1.22 1.773-1.22 3.16v3.199l8.6-.439z" fill="#e4d1eb" data-original="#e7adfb" />
                    </g>
                    </svg>
                    After Effects
                  </div>
                  <span className="status">
                    <span className="status-circle green"></span>
                    Updated</span>
                  <div className="button-wrapper">
                    <button className="content-button status-button open">Open</button>
                    <div className="menu">
                      <DropdownMenu />
                    </div>
                  </div>
                  </li>
              </ul>
            </div>
            <div className="content-section">
            <div className="content-section-title">Apps in your plan</div>
            <div className="apps-card">
              <div className="app-card">
              <span>
                <svg viewBox="0 0 512 512" :style="{ border: '1px solid #a059a9' }">
                <path xmlns="http://www.w3.org/2000/svg" d="M480 0H32C14.368 0 0 14.368 0 32v448c0 17.664 14.368 32 32 32h448c17.664 0 32-14.336 32-32V32c0-17.632-14.336-32-32-32z" fill="#210027" data-original="#7b1fa2" />
                <g xmlns="http://www.w3.org/2000/svg">
                  <path d="M192 64h-80c-8.832 0-16 7.168-16 16v352c0 8.832 7.168 16 16 16s16-7.168 16-16V256h64c52.928 0 96-43.072 96-96s-43.072-96-96-96zm0 160h-64V96h64c35.296 0 64 28.704 64 64s-28.704 64-64 64zM400 256h-32c-18.08 0-34.592 6.24-48 16.384V272c0-8.864-7.168-16-16-16s-16 7.136-16 16v160c0 8.832 7.168 16 16 16s16-7.168 16-16v-96c0-26.464 21.536-48 48-48h32c8.832 0 16-7.168 16-16s-7.168-16-16-16z" fill="#f6e7fa" data-original="#e1bee7" />
                </g>
                </svg>
                Premiere Pro
              </span>
              <div className="app-card__subtext">Edit, master and create fully proffesional videos</div>
              <div className="app-card-buttons">
                <button className="content-button status-button">Update</button>
                <div className="menu"></div>
              </div>
              </div>
              <div className="app-card">
              <span>
                <svg viewBox="0 0 52 52" :style="{ border: '1px solid #c1316d' }">
                <g xmlns="http://www.w3.org/2000/svg">
                  <path d="M40.824 52H11.176C5.003 52 0 46.997 0 40.824V11.176C0 5.003 5.003 0 11.176 0h29.649C46.997 0 52 5.003 52 11.176v29.649C52 46.997 46.997 52 40.824 52z" fill="#2f0015" data-original="#6f2b41" />
                  <path d="M18.08 39H15.2V13.72l-2.64-.08V11h5.52v28zM27.68 19.4c1.173-.507 2.593-.761 4.26-.761s3.073.374 4.22 1.12V11h2.88v28c-2.293.32-4.414.48-6.36.48-1.947 0-3.707-.4-5.28-1.2-2.08-1.066-3.12-2.92-3.12-5.561v-7.56c0-2.799 1.133-4.719 3.4-5.759zm8.48 3.12c-1.387-.746-2.907-1.119-4.56-1.119-1.574 0-2.714.406-3.42 1.22-.707.813-1.06 1.847-1.06 3.1v7.12c0 1.227.44 2.188 1.32 2.88.96.719 2.146 1.079 3.56 1.079 1.413 0 2.8-.106 4.16-.319V22.52z" fill="#e1c1cf" data-original="#ff70bd" />
                </g>
                </svg>
                InDesign
              </span>
              <div className="app-card__subtext">Design and publish great projects & mockups</div>
              <div className="app-card-buttons">
                <button className="content-button status-button">Update</button>
                <div className="menu"></div>
              </div>
              </div>
              <div className="app-card">
              <span>
                <svg viewBox="0 0 52 52" :style="{ border: '1px solid #C75DEB' }">
                <g xmlns="http://www.w3.org/2000/svg">
                  <path d="M40.824 52H11.176C5.003 52 0 46.997 0 40.824V11.176C0 5.003 5.003 0 11.176 0h29.649C46.997 0 52 5.003 52 11.176v29.649C52 46.997 46.997 52 40.824 52z" fill="#3a3375" data-original="#3a3375" />
                  <path d="M27.44 39H24.2l-2.76-9.04h-8.32L10.48 39H7.36l8.24-28h3.32l8.52 28zm-6.72-12l-3.48-11.36L13.88 27h6.84zM31.48 33.48c0 2.267 1.333 3.399 4 3.399 1.653 0 3.466-.546 5.44-1.64L42 37.6c-2.054 1.254-4.2 1.881-6.44 1.881-4.64 0-6.96-1.946-6.96-5.841v-8.2c0-2.16.673-3.841 2.02-5.04 1.346-1.2 3.126-1.801 5.34-1.801s3.94.594 5.18 1.78c1.24 1.187 1.86 2.834 1.86 4.94V30.8l-11.52.6v2.08zm8.6-5.24v-3.08c0-1.413-.44-2.42-1.32-3.021-.88-.6-1.907-.899-3.08-.899-1.174 0-2.167.359-2.98 1.08-.814.72-1.22 1.773-1.22 3.16v3.199l8.6-.439z" fill="#e4d1eb" data-original="#e7adfb" />
                </g>
                </svg>
                After Effects
              </span>
              <div className="app-card__subtext">Industry Standart motion graphics & visual effects</div>
              <div className="app-card-buttons">
                <button className="content-button status-button">Update</button>
                <div className="menu"></div>
              </div>
              </div>
            </div>
            </div>
          </div>
          </div>
        </div>
        <div className="overlay-app"></div>
        </div>
    <!-- <RouterView /> -->
  </div>
</template>

<style >
.notification {
  position: relative;
}
.notification-number {
  position: absolute;
  background-color: #3a6df0;
  width: 16px;
  height: 16px;
  border-radius: 50%;
  font-size: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  right: -6px;
  top: -6px;
}
.notification + svg {
  margin-left: 22px;
}
@media screen and (max-width: 945px) {
  .notification + svg {
    display: none;
  }
}


.wrapper {
  display: flex;
  flex-grow: 1;
  overflow: hidden;
}

.updates {
  position: relative;
  top: 0;
  right: 0;
  margin-left: auto;
  width: 18px;
  height: 18px;
  font-size: 11px;
}

.main-container {
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

.content-wrapper {
  display: flex;
  flex-direction: column;
  color: var(--theme-color);
  padding: 20px 40px;
  height: 100%;
  overflow: auto;
  background-color: var(--theme-bg-color);
}
@media screen and (max-width: 510px) {
  .content-wrapper {
    padding: 20px;
  }
}
.content-wrapper-header {
  display: flex;
  align-items: center;
  width: 100%;
  justify-content: space-between;
  background-image: url("https://www.transparenttextures.com/patterns/cubes.png"), linear-gradient(to right top, #cf4af3, #e73bd7, #f631bc, #fd31a2, #ff3a8b, #ff4b78, #ff5e68, #ff705c, #ff8c51, #ffaa49, #ffc848, #ffe652);
  border-radius: 14px;
  padding: 20px 40px;
}
@media screen and (max-width: 415px) {
  .content-wrapper-header {
    padding: 20px;
  }
}
.content-wrapper.overlay {
  pointer-events: none;
  transition: 0.3s;
  background-color: var(--overlay-bg);
}

.overlay-app {
  width: 100%;
  height: 100%;
  position: fixed;
  left: 0;
  top: 0;
  pointer-events: all;
  background-color: rgba(236, 39, 59, 0.8);
  opacity: 0;
  visibility: hidden;
  transition: 0.3s;
}
.overlay-app.is-active {
  visibility: visible;
  opacity: 1;
}

.img-content {
  font-weight: 500;
  font-size: 17px;
  display: flex;
  align-items: center;
  margin: 0;
}
.img-content svg {
  width: 28px;
  margin-right: 14px;
}

.content-text {
  font-weight: 400;
  font-size: 14px;
  margin-top: 16px;
  line-height: 1.7em;
  color: #ebecec;
  display: -webkit-box;
  -webkit-line-clamp: 4;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
}

.content-wrapper-context {
  max-width: 350px;
}

.content-button {
  background-color: #3a6df0;
  border: none;
  padding: 8px 26px;
  color: #fff;
  border-radius: 20px;
  margin-top: 16px;
  cursor: pointer;
  transition: 0.3s;
  white-space: nowrap;
}

.content-wrapper-img {
  width: 186px;
  -o-object-fit: cover;
     object-fit: cover;
  margin-top: -25px;
  -o-object-position: center;
     object-position: center;
}
@media screen and (max-width: 570px) {
  .content-wrapper-img {
    width: 110px;
  }
}

.content-section {
  margin-top: 30px;
  display: flex;
  flex-direction: column;
}
.content-section-title {
  color: var(--content-title-color);
  margin-bottom: 14px;
}
.content-section ul {
  display: flex;
  flex-direction: column;
  width: 100%;
  height: 100%;
  justify-content: space-around;
  background-color: var(--content-bg);
  padding-left: 0;
  margin: 0;
  border-radius: 14px;
  border: 1px solid var(--theme-bg-color);
  cursor: pointer;
}
.content-section ul li {
  list-style: none;
  padding: 10px 18px;
  display: flex;
  align-items: center;
  font-size: 16px;
  width: 100%;
  height: 100%;
  white-space: nowrap;
  transition: 0.3s;
}
.content-section ul li:hover {
  background-color: var(--theme-bg-color);
}
.content-section ul li:hover:first-child {
  border-radius: 13px 13px 0 0;
}
.content-section ul li:hover:last-child {
  border-radius: 0 0 13px 13px;
}
.content-section ul li + li {
  border-top: 1px solid var(--border-color);
}
.content-section ul svg {
  width: 28px;
  border-radius: 6px;
  margin-right: 16px;
  flex-shrink: 0;
}

.products {
  display: flex;
  align-items: center;
  width: 150px;
}
@media screen and (max-width: 480px) {
  .products {
    width: 120px;
  }
}

.status {
  margin-left: auto;
  width: 140px;
  font-size: 15px;
  position: relative;
}
@media screen and (max-width: 700px) {
  .status {
    display: none;
  }
}
.status-circle {
  width: 6px;
  height: 6px;
  background-color: #396df0;
  position: absolute;
  border-radius: 50%;
  top: 4px;
  left: -20px;
}
.status-circle.green {
  background-color: #3bf083;
}
.status-button {
  font-size: 15px;
  margin-top: 0;
  padding: 6px 24px;
}
@media screen and (max-width: 390px) {
  .status-button {
    padding: 6px 14px;
  }
}
.status-button.open {
  background: none;
  color: var(--button-inactive);
  border: 1px solid var(--button-inactive);
}
.status-button:not(.open):hover {
  color: #fff;
  border-color: #fff;
}

.content-button:not(.open):hover {
  background: #1e59f1;
}

.menu {
  width: 5px;
  height: 5px;
  background-color: var(--button-inactive);
  border-radius: 50%;
  box-shadow: 7px 0 0 0 var(--button-inactive), 14px 0 0 0 var(--button-inactive);
  margin: 0 12px;
}

@media screen and (max-width: 415px) {
  .adobe-product .menu {
    display: none;
  }
}


.button-wrapper {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  width: 187px;
  margin-left: auto;
}
@media screen and (max-width: 480px) {
  .button-wrapper {
    width: auto;
  }
}


.content-button-wrapper .content-button.status-button.open.close {
  width: auto;
}

.content-section .close {
  margin-right: 0;
  width: 24px;
}

.checkbox-wrapper {
  display: flex;
  align-items: center;
  font-size: 14px;
  font-weight: 400;
}
.checkbox-wrapper + .checkbox-wrapper {
  margin: 20px 0 40px;
}

.checkbox {
  display: none;
}

.checkbox + label {
  display: flex;
  align-items: center;
}
.checkbox + label:before {
  content: "";
  margin-right: 10px;
  width: 15px;
  height: 15px;
  border: 1px solid var(--theme-color);
  border-radius: 4px;
  cursor: pointer;
  flex-shrink: 0;
}

.checkbox:checked + label:before {
  background-color: #3a6df0;
  border-color: #3a6df0;
  background-image: url("data:image/svg+xml;charset=UTF-8,%3csvg xmlns='http://www.w3.org/2000/svg' width='24' height='24' viewBox='0 0 24 24' fill='none' stroke='%23fff' stroke-width='3' stroke-linecap='round' stroke-linejoin='round' class='feather feather-check'%3e%3cpath d='M20 6L9 17l-5-5'/%3e%3c/svg%3e");
  background-position: 50%;
  background-size: 12px;
  background-repeat: no-repeat;
}

.content-button-wrapper {
  margin-top: auto;
  margin-left: auto;
}
.content-button-wrapper .open {
  margin-right: 8px;
}

.apps-card {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  width: calc(100% + 20px);
}

.app-card {
  display: flex;
  flex-direction: column;
  width: calc(33.3% - 20px);
  font-size: 16px;
  background-color: var(--content-bg);
  border-radius: 14px;
  border: 1px solid var(--theme-bg-color);
  padding: 20px;
  cursor: pointer;
  transition: 0.3s ease;
}
.app-card:hover {
  transform: scale(1.02);
  background-color: var(--theme-bg-color);
}
.app-card svg {
  width: 28px;
  border-radius: 6px;
  margin-right: 12px;
  flex-shrink: 0;
}
.app-card + .app-card {
  margin-left: 20px;
}
.app-card span {
  display: flex;
  align-items: center;
}
.app-card__subtext {
  font-size: 14px;
  font-weight: 400;
  line-height: 1.6em;
  margin-top: 20px;
  border-bottom: 1px solid var(--border-color);
  padding-bottom: 20px;
}
.app-card-buttons {
  display: flex;
  align-items: center;
  margin-left: auto;
  margin-top: 16px;
}
@media screen and (max-width: 1110px) {
  .app-card {
    width: calc(50% - 20px);
  }
  .app-card:last-child {
    margin-top: 20px;
    margin-left: 0px;
  }
}
@media screen and (max-width: 565px) {
  .app-card {
    width: calc(100% - 20px);
    margin-top: 20px;
  }
  .app-card + .app-card {
    margin-left: 0;
  }
}

::-webkit-scrollbar {
  width: 6px;
  border-radius: 10px;
}

::-webkit-scrollbar-thumb {
  background: var(--scrollbar-bg);
  border-radius: 10px;
}
</style>

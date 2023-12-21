<script setup>
import { RouterView } from "vue-router";
</script>

<template>
  <div class="wrapper">
    <div class="people">
      <header>Ваши сообщения</header>
      <ul class="people-list">
        <li>
          <div class="people-item active">
            <div class="people-avatar">
              <img src="./assets/people-ava.png" alt="ava" />
            </div>
            <div>
              <h2>Баланчаева Б.Б.</h2>
              <span>онлайн</span>
            </div>
          </div>
        </li>
        <li>
          <div class="people-item">
            <div class="people-avatar">
              <img src="./assets/people-ava.png" alt="ava" />
            </div>
            <div>
              <h2>Баланчаева Б.Б.</h2>
              <span>онлайн</span>
            </div>
          </div>
        </li>
        <li>
          <div class="people-item">
            <div class="people-avatar">
              <img src="./assets/people-ava.png" alt="ava" />
            </div>
            <div>
              <h2>Баланчаева Б.Б.</h2>
              <span>онлайн</span>
            </div>
          </div>
        </li>
      </ul>
    </div>
    <router-view />
  </div>
</template>

<style lang="scss">
.wrapper {
  display: flex;
  margin: 0 auto;
  max-width: 70%;
  padding: 40px;
  gap: 30px;
}
.people {
  max-width: 365px;
  header {
    background: #efefef;
    color: #24334b;
    font-size: 18px;
    font-weight: 600;
    padding: 16px;
    line-height: 18px; /* 100% */
  }
  li {
    padding: 16px 0;
  }
  &-item {
    display: flex;
    align-items: center;
    gap: 16px;
    padding: 16px;
    cursor: pointer;
    &-avatar {
      width: 40px;
      height: 40px;
      border-radius: 100%;
      overflow: hidden;

      img {
        max-height: 100%;
        max-width: 100%;
      }
    }

    h2 {
      color: #24334b;
      font-size: 16px;
      font-weight: 500;
      margin: 0;
    }
    span {
      color: #bdbdbd;
      font-size: 14px;
      font-weight: 500;
    }

    &.active {
      background: #24334b;
      box-shadow: 0px 10px 20px 0px #acbbd2;
      h2 {
        color: #f6f6f6;
      }
      span {
        color: #1baa75;
      }
    }
  }
}
</style>

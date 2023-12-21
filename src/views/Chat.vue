<template>
  <div class="chat">
    <header>
      <div class="chat-info">
        <div class="chat-avatar">
          <img src="../assets/people-ava.png" alt="ava" />
        </div>
        <div>
          <h2>Баланчаева Б.Б.</h2>
          <span>онлайн</span>
        </div>
      </div>
      <svg
        width="24"
        height="24"
        viewBox="0 0 24 24"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="M12 14C13.1046 14 14 13.1046 14 12C14 10.8954 13.1046 10 12 10C10.8954 10 10 10.8954 10 12C10 13.1046 10.8954 14 12 14Z"
          fill="white"
        />
        <path
          d="M12 7C13.1046 7 14 6.10457 14 5C14 3.89543 13.1046 3 12 3C10.8954 3 10 3.89543 10 5C10 6.10457 10.8954 7 12 7Z"
          fill="white"
        />
        <path
          d="M12 21C13.1046 21 14 20.1046 14 19C14 17.8954 13.1046 17 12 17C10.8954 17 10 17.8954 10 19C10 20.1046 10.8954 21 12 21Z"
          fill="white"
        />
      </svg>
    </header>
    <ul class="messages">
      <li
        v-for="(item, i) in messageList"
        class="message"
        :class="item.userId === 'me' ? 'me' : ''"
        :key="i"
      >
        <div class="message-text">
          {{ item.text }}
        </div>
        <div class="message-time">
          {{ item.time }}
          <svg
            v-if="item.userId === 'me'"
            xmlns="http://www.w3.org/2000/svg"
            width="16"
            height="17"
            viewBox="0 0 16 17"
            fill="none"
          >
            <path
              d="M7.7345 9.67366L8.67584 10.615L14.3198 4.97099L15.2625 5.91366L8.67584 12.5003L4.43317 8.25766L5.37584 7.31499L6.7925 8.73166L7.7345 9.67299V9.67366ZM7.73584 7.78833L11.0372 4.48633L11.9772 5.42633L8.67584 8.72833L7.73584 7.78833ZM5.85117 11.5583L4.90917 12.5003L0.666504 8.25766L1.60917 7.31499L2.55117 8.25699L2.5505 8.25766L5.85117 11.5583Z"
              fill="#F6F6F6"
            />
          </svg>
        </div>
      </li>
    </ul>
    <select id="user" v-model="selectedUser">
      <option value="dis" disabled>Выберите userId</option>
      <option value="me">Я</option>
      <option value="companion" selected>Собеседник</option>
    </select>
    <label>
      <textarea type="text" placeholder="Ваше сообщение" v-model="message" />
      <div class="send" @click="sendMessage()">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="30"
          height="30"
          viewBox="0 0 30 30"
          fill="none"
        >
          <path
            d="M25.7345 14.1654L5.10954 3.85292C4.94789 3.77207 4.76631 3.73968 4.58668 3.75964C4.40704 3.7796 4.23701 3.85106 4.09704 3.96542C3.96338 4.07744 3.86361 4.22453 3.80896 4.39015C3.7543 4.55576 3.74693 4.73334 3.78767 4.90292L6.56267 14.9998L3.75017 25.0685C3.71194 25.2102 3.70748 25.3588 3.73714 25.5024C3.7668 25.6461 3.82975 25.7808 3.92094 25.8957C4.01213 26.0106 4.129 26.1024 4.26217 26.164C4.39533 26.2255 4.54107 26.2549 4.68767 26.2498C4.83442 26.2489 4.97893 26.2136 5.10954 26.1467L25.7345 15.8342C25.8881 15.7555 26.017 15.636 26.107 15.4888C26.197 15.3415 26.2446 15.1723 26.2446 14.9998C26.2446 14.8272 26.197 14.6581 26.107 14.5108C26.017 14.3636 25.8881 14.2441 25.7345 14.1654ZM6.14079 23.5404L8.21267 15.9373H16.8752V14.0623H8.21267L6.14079 6.45917L23.2127 14.9998L6.14079 23.5404Z"
            fill="#F6F6F6"
          />
        </svg>
      </div>
    </label>
  </div>
</template>

<script setup>
import { ref } from "vue";

const messageList = ref([
  {
    userId: "me",
    time: "16:29",
    text: `Здравствуйте! Я оставил вам заявку на доверенность`,
    check: true,
  },
  {
    userId: "companion",
    time: "16:29",
    text: `Здравствуйте! Ваши документы готовы. Вам необходимо подойти в наш офис на Московская 25, подписать и забрать Доверенность.`,
    check: true,
  },
  {
    userId: "me",
    time: "16:29",
    text: `Хорошо, спасибо, я подойду завтра утром.`,
    check: true,
  },
]);

const userId = ref("");
const message = ref("");
const selectedUser = ref("dis");

const sendMessage = () => {
  let newMessage = ref({
    userId: selectedUser.value,
    time: "16:29",
    text: message.value,
    check: true,
  });
  if (selectedUser.value && message.value && selectedUser.value !== "dis") {
    messageList.value.push(newMessage.value);
    userId.value = "";
    message.value = "";
  }
};
</script>

<style lang="scss">
.chat {
  flex: 1;

  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: #3f5984;
    padding: 16px;

    svg {
      cursor: pointer;
    }

    .chat-avatar {
      cursor: pointer;
    }
  }

  &-info {
    display: flex;
    align-items: center;
    gap: 16px;

    h2 {
      color: #f6f6f6;
      font-size: 16px;
      font-weight: 500;
    }

    span {
      color: #1baa75;
      font-size: 14px;
      font-weight: 500;
    }
  }

  li {
    margin-bottom: 11px;
  }
  .message.me {
    background: #1baa75;
    max-width: 45%;
    margin-left: auto;
    color: #f6f6f6;
    font-size: 14px;
    line-height: 140%;

    .message-text {
      padding: 15px 15px 0 15px;
    }

    .message-time {
      font-size: 12px;
      display: flex;
      align-items: center;
      justify-content: flex-end;
      gap: 5px;
      padding: 5px;
    }
  }

  select {
    margin-bottom: 5px;
  }
  .message {
    background: #efefef;
    max-width: 50%;
    color: #24334b;
    font-size: 14px;
    line-height: 140%;

    .message-text {
      padding: 15px 15px 0 15px;
    }

    .message-time {
      font-size: 12px;
      display: flex;
      align-items: center;
      justify-content: flex-end;
      gap: 5px;
    }
  }

  label {
    display: flex;
    align-items: center;

    textarea {
      flex: 1;
      resize: none;
      padding: 22px 15px;
      box-sizing: border-box;
      height: 64px;
      font-family: "Montserrat";
    }

    .send {
      padding: 15px 25px;
      background: #1baa75;
      cursor: pointer;
    }
  }
}
</style>
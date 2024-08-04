<template>
  <div class="main-wrapper">
    <div class="chat-header">
      <div class="header-content">
        <Select v-model="selectedCity" :options="models" optionLabel="name" optionValue="code" placeholder="Select a model" />
      </div>
    </div>
    <div class="chat-content">
      <div class="message-container" v-for="a in 10" :key="a" :class="{'chatbot-message': a % 2 === 0, 'user-message': a % 2 !== 0}">
        <div class="avatar-wrapper">
          <img src="https://letstryai.com/wp-content/uploads/2023/11/stable-diffusion-avatar-prompt-example-6.jpg" class="avatar" />
        </div>
        <div class="message-wrapper">Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.</div>
        <div class="message-actions"></div>
      </div>
    </div>
    <div class="chat-footer">
      <div class="input-container">
        <InputText type="text" v-model="value" placeholder="Write your prompt here..." size="large" class="main-input" />
        <Button label="Send" icon="fas fa-send" class="send-btn" />
      </div>
      <div class="disclaimer-text">
      </div>
    </div>
  </div>
</template>

<script setup>
import InputText from 'primevue/inputtext';
import Button from 'primevue/button';
import Select from 'primevue/select';
import { ref } from 'vue'
import { useLanguage } from "../utils/language";
const { switchLanguage } = useLanguage();


const models = [
  { name: 'llama-v3', code: 'M1' },
  { name: 'mistral', code: 'M2' },
  { name: 'Model 3', code: 'M3' },
  { name: 'Model 4', code: 'M4' }
];

const selectedCity = ref("M1");
</script>

<style lang="scss" scoped>

.main-wrapper {
  display: flex;
  flex-direction: column;
  flex: 1 0 0;
  justify-content: space-between;
  height: 100%;
  width: 100%;
  max-height: 100vh;
  overflow: auto;

  .chat-header {
    display: flex;
    flex-direction: column;
    margin: 1rem;
    margin-bottom: 0;
    height: 3rem;
    border-bottom: 1px solid var(--p-divider-border-color);

    .header-content {
      display: flex;
      flex-direction: row;
      overflow: hidden;
    }
  }

  .chat-content {
    flex: 1 0 0;
    overflow: auto;
    padding: 1rem;
    width: 100%;
    max-width: 45rem;
    margin: 0 auto;

    .message-container {
      display: flex;
      flex-direction: row;
      align-items: flex-start;
      margin-bottom: 1rem;

      &.chatbot-message {
        flex-direction: row;

        .avatar-wrapper {
          margin-right: 1rem;
          margin-left: 0;
        }
      }

      &.user-message {
        flex-direction: row-reverse;

        .avatar-wrapper {
          margin-left: 1rem;
          margin-right: 0;
        }

        .message-wrapper {
          background-color: var(--p-inputtext-focus-border-color);
        }
      }

      .avatar-wrapper {
        position: relative;
        font-size: 0.4em;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;

        .avatar {
          width: 3rem;
          height: 3rem;
          border-radius: 50%;
        }
      }

      .message-wrapper {
        display: flex;
        flex-direction: column;
        justify-content: center;
        padding: 1rem;
        border-radius: 1rem;
        border: 1px solid var(--p-inputtext-focus-border-color);
        border-radius: 1rem;
      }

      .message-actions {
        display: flex;
        flex-direction: row;
        justify-content: flex-end;
        margin-top: 1rem;
      }
    }
  }

  .chat-footer {
    width: 100%;
    max-width: 100%;
    padding: 2rem;
    display: flex;
    flex-direction: column;

    .input-container {
      display: flex;
      justify-content: center;

      .main-input {
        width: 100%;
        max-width: 40rem;
        border-right: none;
        border-top-right-radius: 0;
        border-bottom-right-radius: 0;
      }

      .send-btn {
        border-top-left-radius: 0;
        border-bottom-left-radius: 0;
      }
    }
  }
}
</style>

<template>
  
  <div class="message-list">
    <div v-for="message in messages" :key="message.sid" class="message">
      <div class="message-header">
        <span class="message-from">{{ message.from }}</span>
        <span class="message-date">{{ message.date }}</span>
      </div>
      <div class="message-body">{{ message.body }}</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      messages: [],
    };
  },
  methods: {
    async fetchMessages() {
      try {
        const response = await fetch('http://localhost:3000/messages');
          const messages = await response.json();
          this.messages = messages;
      } catch (error) {
        console.error(error);
        this.error = 'Error fetching messages';
      }
    },
  },
  mounted() {
    this.fetchMessages();
  },
};
</script>

<style scoped>
.message-list {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.message {
  display: flex;
  flex-direction: column;
  background-color: #f5f5f5;
  border-radius: 8px;
  padding: 16px;
}

.message-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.message-from {
  font-weight: bold;
}

.message-date {
  font-size: 12px;
}

.message-body {
  margin-top: 16px;
}
</style>

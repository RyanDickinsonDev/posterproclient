<template>
    <div class="container">
    <h1>Poster Pro v1</h1>
    <p>Custom Messaging Solution By: Ryan Dickinson</p>
    <form>
      <label for="message">Message:</label>
      <textarea v-model="message"></textarea>

      <button @click.prevent="send">Send</button>
      <div v-if="showMessage">
        <p id="success-message">{{ success.message }}</p>
      </div>
    </form>
  </div>

</template>

<script>


export default {
  data() {
    return {
      message: '',
      success: '',
      showMessage: false,
    };
  },
  methods: {
    send() {
      const url = 'http://localhost:3000/send';
      const data = { message: this.message };

      fetch(url, {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(data)
      }).then((response) => response.json())
      .then((json) => this.success = json);
      this.showMessage = true;
    },
  },
};
</script>

<style scoped>

.container{
  padding: 20px;
}

div {
  max-width: 800px;
  margin: 0 auto;
}

h1 {
  font-size: 32px;
  margin-bottom: 16px;
  text-align: center;
}

form {
  border: 1px solid #ccc;
  border-radius: 8px;
  padding: 16px;
  margin-bottom: 16px;
}

label {
  display: block;
  font-size: 16px;
  font-weight: bold;
  margin-bottom: 8px;
}

input[type="text"],
textarea {
  padding: 8px;
  margin-bottom: 16px;
  border-radius: 4px;
  border: 1px solid #ccc;
  width: 100%;
}

button {
  padding: 8px 16px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.2s ease;
}

button:hover {
  background-color: #0062cc;
}

#success-message{
  background-color: #fff;
  color: red;
  text-align: center;
  font-weight: bold;
  font-size: 28px;

}
</style>
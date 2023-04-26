<template>
  <div id="app">
    <MessageSender />
    <MessageList />
  </div>
</template>

<script>
import MessageSender from './components/MessageSender.vue'
import MessageList from './components/MessageList.vue'

export default {
  name: 'App',
  components: {
   MessageSender,
   MessageList,
  }
}
</script>

<style>
#app {
  margin-left: 50px;
  margin-right: 50px;
  padding: 0;
}
</style>

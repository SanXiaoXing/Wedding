<template>
  <div>
    <h1>
      <Typewriter :texts="messages" :typingSpeed="200" />
    </h1> 
  </div>
</template>

<script>
import Typewriter from '../components/typedText.vue'; // 引入逐字显示组件

export default {
  components: {
    Typewriter
  },
  data() {
    return {
      messages: ['Hello, World!', 'I am Vue.js.', 'Welcome to the chat.']
    };
  }
};
</script>
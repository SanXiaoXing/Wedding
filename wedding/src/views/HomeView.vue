<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/Lover.svg">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <Card></Card>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import Card from '@/components/Card.vue';

export default {
  name: 'HomeView',
  components: {
    HelloWorld,
    Card
  }
}
</script>

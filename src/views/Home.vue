<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <div>{{ message }}</div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue';

export default {
  name: 'Home',
  components: {
    HelloWorld,
  },
  data() {
    return {message: 'hello'};
    },
  methods: {
    increment() {
      this.$store.commit('increment');
      // console.log(this.$store.state.count);

    },
    },
};

</script>

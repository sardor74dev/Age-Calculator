<template>
  <div id="app">
    <v-app>
        <DateOfBirth/>
    </v-app>
  </div>
</template>

<script>
import DateOfBirth from './components/DateOfBirth.vue';

export default {
  name: 'App',

  components: {
    DateOfBirth,
  },

  data: () => ({

  }),
 
}
</script>
<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: white;
  max-width: 992px;
  margin: 0px auto;
  padding: 15px 15px;
  overflow: hidden;
  height: 100%;
}
</style>

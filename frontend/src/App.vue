<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Hello Vue 3 + TypeScript + Vit2e" />
  <p>'ABC': {{repositories}}</p>
</template>

<script lang="ts">

import { defineComponent } from 'vue'
import HelloWorld from './components/HelloWorld.vue'
import { ref, onMounted } from 'vue'

export default defineComponent({
  name: 'App',
  components: {
    HelloWorld
  },
  data() {
    return {
      repositories: []
    }
  },
  async mounted() {

     const response = await fetch(`http://localhost:5000/weatherforecast`,{
            mode: 'no-cors',
            headers: {
              'Access-Control-Allow-Origin':'*'
            }
          })
          console.log("response", await response.json())

          this.repositories = await response.json();
    }
  // setup(props) {
  //   console.log(props) // { user: '' }

  //   const repositories = ref([])
  //   const getUserRepositories = async () => {
  //     repositories.value = await fetch(`${process.env.VUE_API_URL}/weatherforecast`)
  //   }

  //   onMounted(getUserRepositories)

  //   return {
  //     repositories,
  //     getUserRepositories
  //   }
  // }
})
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
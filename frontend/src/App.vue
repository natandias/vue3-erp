<template>
    <Navbar />
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import { ref, onMounted } from 'vue'
import Navbar from './components/layout/Navbar.vue'

export default defineComponent({
    name: 'App',
    components: { Navbar },
    data() {
        return {
            repositories: [],
        }
    },
    async mounted() {
        const response = await fetch(`http://localhost:5000/weatherforecast`, {
            mode: 'no-cors',
            headers: {
                'Access-Control-Allow-Origin': '*',
            },
        })
        console.log('response', await response.json())

        this.repositories = await response.json()
    },
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

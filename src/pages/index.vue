<template>
  <div class="indexMargin">
    <h1>This is the Front Page.</h1>
    <h3>The chosen one is called {{ chosenOne }}</h3>
    <button v-on:click="showAlert">Show alert</button>
    <button v-on:click="counter += 1">Add 1</button>
    <p>The button above has been clicked {{ counter }} times.</p>

  </div>
</template>

<script>
  import axios from 'axios';

  export default {
    async asyncData ({ params }) {
      let { data } = await axios.get('https://swapi.co/api/people/1/')
      return { chosenOne: data.name }
    },

    computed: {
      theName () {
        return this.name || 'anon'
      }
    },
    data: function() {
      return {
        counter: 1,
      }
    },
    methods: {
      showAlert: function() {
        alert("Button worked");
      },
    },
    head: {
      link: [
        {
          rel: 'stylesheet', href: 'https://cdnjs.cloudflare.com/ajax/libs/semantic-ui/1.11.8/semantic.min.css'
        }
      ]
    }
  }
</script>

<style scoped>
  .indexMargin {
    margin: 15px
  }
</style>



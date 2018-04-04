<template>
  <div id="app">
    <ul>
      <li 
        v-for="user in users" 
        :key="user.email">
        {{ user.email }}
      </li>
    </ul>
  </div>
</template>

<script>
import gql from 'graphql-tag'

export default {
  name: 'app',

  data () {
    return {
      users: [
        //
      ]
    }
  },

  apollo: {
    users: gql`
      {
        allUsers {
          email
        }
      }
    `
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>

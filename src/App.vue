<template type="text/html">
  <div id="app">
    <input 
      v-model="id" 
      type="text" 
      class="query__input" />

    <div v-if="$apollo.loading">
        Loading...
    </div>

    <div v-else>
      <pre v-html="User"></pre>
      
      <pre v-html="allUsers"></pre>

      <ul>
        <li 
          v-for="user in allUsers" 
          :key="user.email">
          <a :href="`mailto:${ user.email }`">
            {{ user.firstName }}&nbsp;{{ user.lastName }}
          </a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import gql from 'graphql-tag'

const allUsersQuery = gql`query allUsersQuery {
  allUsers {
    email
    firstName
    lastName
  }
}`

const userQuery = {
  query: gql`query userQuery($id: ID!) {
    User(id: $id) {
      firstName
      lastName
    }
  }`,
  variables () {
    return {
      id: this.id
    }
  }
}

export default {
  name: 'app',

  data () {
    return {
      id: 1,
      User: {
        //
      },
      allUsers: [
        //
      ]
    }
  },

  apollo: {
    User: userQuery,
    allUsers: allUsersQuery
  }
}
</script>

<template type="text/html">
  <div id="app">
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
</template>

<script>
import gql from 'graphql-tag'

const allUsersQuery = gql`{
  allUsers {
    email
    firstName
    lastName
  }
}`

const userQuery = {
  query: gql`query getUser($id: ID!) {
    User(id: $id) {
      firstName
      lastName
    }
  }`,
  variables: {
    id: 1
  }
}

export default {
  name: 'app',

  data () {
    return {
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

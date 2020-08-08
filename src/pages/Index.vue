<template>
  <q-page class="flex flex-center">
    <img
      alt="Quasar logo"
      src="~assets/quasar-logo-full.svg"
    >
    <div v-if="posts">GraphQL query result:<br />
      <ul>
        <li v-for="post in posts">{{post.title}}</li>
      </ul>
    </div>
    <div v-else>Loading...</div>
  </q-page>
</template>

<script>
import gql from 'graphql-tag'
export default {
  name: 'PageIndex',
  data: () => ({
    posts: []
  }),
  apollo: {
    posts: {
      query: gql`
          query {
            posts {
              id
              title
              author {
                first_name
                last_name
              }
              comments {
                id
                reply
              }
            }
          }
        `
    }
  }
}
</script>

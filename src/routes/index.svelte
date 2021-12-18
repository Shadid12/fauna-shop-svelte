<script>
  import { query } from "svelte-apollo";
  import { gql } from "@apollo/client/core";
  const GET_POSTS = gql`
    {
    listPosts {
      data {
        id
        title
        author {
          _id
          name
        }
        tags
      }
      after
      before
    }
  }
  `;

  const posts = query(GET_POSTS);
  console.log(posts);
</script>

<h1>Welcome to SvelteKit</h1>
{#await $posts}
  Loading...
{:then result}
{JSON.stringify(result)}
{:catch error}
{error}
{/await}
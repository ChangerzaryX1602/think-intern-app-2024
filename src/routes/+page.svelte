<script>
  import axios from "axios";
  import { onMount } from "svelte";
  let ImageURL = "";
  const requestAPI = async () => {
    try {
      const response = await axios.get(
        "https://api.thecatapi.com/v1/images/search"
      );
      if (response.data && response.data.length > 0) {
        ImageURL = response.data[0].url;
      }
      console.log("Hi");
    } catch (error) {
      console.error(error);
    }
  };
  onMount(() => {
    requestAPI();
  });
</script>

<button class="cat" tabindex="0" aria-label="Get a random cat image" on:click={requestAPI}>
  {#if ImageURL}
    <img src={ImageURL} alt="random img" />
  {:else}
    <p>Loading...</p>
  {/if}
</button>

<style lang="postcss">
  :global(html) {
    background-color: theme(colors.gray.100);
  }
  .cat{
    display: flex;
    justify-content: center;
    height: 100vh;
  }
</style>

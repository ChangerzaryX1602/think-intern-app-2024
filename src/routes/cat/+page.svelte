<script>
    import axios from "axios";
    import { onMount } from "svelte";
    let ImageURL = "";
    const requestAPI = async () => {
      try {
        ImageURL = "";
        const response = await axios.get(
          "https://api.thecatapi.com/v1/images/search"
        );
        if (response.data && response.data.length > 0) {
          ImageURL = response.data[0].url;
        }
      } catch (error) {
        console.error(error);
      }
    };
    onMount(() => {
      requestAPI();
    });
  </script>
  
  <button
    class="cat"
    tabindex="0"
    aria-label="Get a random cat image"
    on:click={requestAPI}
  >
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
    .cat {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 100vw; /* Full viewport width */
      height: 100vh; /* Full viewport height */
    }
  </style>
  
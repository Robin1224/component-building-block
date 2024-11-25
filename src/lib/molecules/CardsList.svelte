<script>
  import Card from "./Card.svelte";

  export let data;
</script>

<section>
  <h2>Alle methodes ({data.length})</h2>
  <ul>
    {#if data && data.length > 0}
      {#each data as method}
        <Card {method} />
      {/each}
    {/if}
  </ul>
</section>

<style>
  section, ul {
    width: 100%;
  }

  ul {
    display: grid;
    grid-template-columns: 100%;
    grid-template-rows: auto;
    margin: 1rem 0;
    container-type: inline-size;
  }

  @media screen and (min-width: 36em) {
    ul {
      grid-template-columns: repeat(2, 1fr);
      gap: 1.5rem;
    }
  }

  @media screen and (min-width: 60em) {
    ul {
      grid-template-columns: repeat(3, auto);
    }
  }
</style>

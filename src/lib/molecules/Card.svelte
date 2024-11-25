<script>
  import Button from "$lib/atoms/Button.svelte";
  import Arrows from "$lib/icons/Arrows.svelte";

  export let method;
</script>

<li>
  <a href="/tekenmethodes/{method.slug}">
    {#if method.template && method.template.url}
      <img
        src={method.template.url.replace(":webp", ":png")}
        alt={"Voorbeeld van " + method.title}
        class={method.categories[0].title.replaceAll(" ", "-")}
      />
    {:else}
      <img
        class={method.categories[0].title.replaceAll(" ", "-")}
        src="/placeholder.webp"
        alt="Placeholder"
      />
    {/if}

    <h3>{method.title}</h3>
    <Button className="card-button">
      <Arrows styles="transform: translateY(2px) translateX(1px);" />
    </Button>
  </a>
</li>

<style>
  li {
    list-style: none;
    width: 100%;
  }

  a {
    text-decoration: none;
    color: black;
    margin-bottom: 5px;
    padding: 0.8em;
    border-bottom: 1px solid #ccc;
    display: grid;
    grid-template-columns: 10rem 1fr;
    grid-template-rows: 1fr 1fr;
    grid-template-areas:
      "img title"
      "img button";
  }

  img {
    width: 10rem;
    height: auto;

    grid-area: img;
  }

  h3 {
    font-family: var(--vtPrimaryFont);
    color: var(--vtDarkBlue);
    font-size: 24px;
    font-weight: 400;
    margin: 0;
    width: 100%;
    padding-left: 1rem;

    grid-area: title;
  }

  :global(.card-button) {
    margin-left: auto;
    margin-top: auto;

    grid-area: button;
  }

  @container (min-width: 36rem) {
  }
</style>

<script>
  import Button from "$lib/atoms/Button.svelte";
  import Arrows from "$lib/icons/Arrows.svelte";

  export let method;
</script>

<li>
  <a href="/tekenmethodes/{method.slug}">
    {#if method.template && method.template.url}
      <img
        loading="lazy"
        src={method.template.url.replace(":webp", ":png")}
        alt={"Voorbeeld van " + method.title}
        class={method.categories[0].title.replaceAll(" ", "-")}
      />
    {:else}
      <img
        loading="lazy"
        class={method.categories[0].title.replaceAll(" ", "-")}
        src="/placeholder.webp"
        alt="Placeholder"
      />
    {/if}

    <h3>{method.title}</h3>
    <button>
      <span>MEER </span><span>LEZEN</span>
      <Arrows />
    </button>
  </a>
</li>

<style>
  li {
    list-style: none;
    width: 100%;
    container-type: inline-size;
    container-name: card;
    transition: background-color 0.2s;
  }

  li:hover {
    background-color: #f3f3f3;
  }

  a {
    text-decoration: none;
    color: black;
    padding: 2rem 1rem;
    border-bottom: 1px solid #ccc;
    margin-bottom: 0;
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
    border-radius: 3px;
    border: 1px solid #ccc;

    grid-area: img;
  }

  h3 {
    font-family: var(--vtPrimaryFont);
    color: var(--vtDarkBlue);
    font-size: 24px;
    font-weight: 400;
    margin: 0;
    /* margin-top: auto; */
    width: 100%;
    padding-left: 1rem;

    grid-area: title;
  }

  button {
    background-color: var(--vtYellow);
    padding: 0.4rem 0.8rem;
    cursor: pointer;
    border-radius: 3px;
    border: none;
    height: fit-content;
    min-width: fit-content;
    max-width: 12rem;
    font-family: var(--vtPrimaryFont);
    color: var(--vtDarkBlue);
    font-size: 1rem;
    font-weight: 400;
    margin-left: 1rem;
    margin-top: auto;
    transition: background-color 0.2s;

    grid-area: button;
  }

  button:hover { 
    background-color: var(--vtYellow-80);
  }

  button > span:nth-child(2) {
    margin-right: 0.2rem;
  }

  button :global(.icon-arrows) {
    transform: translateY(1px);
    height: 0.8rem;
    width: auto;
  }

  @container cards-grid (min-width: 730px) {
    li {
      border: solid 2px var(--vtYellow);
      border-radius: 0.8rem;
      width: 16rem;
      overflow: hidden;
    }

    a {
      border: none;
      grid-template-columns: auto auto;
      grid-template-rows: 1fr auto;
      grid-template-areas:
        "img img"
        "title button";
      padding: 0;
    }

    img {
      width: 16rem;
      height: auto;
      border-radius: 0px;
      border: none;
      border-bottom: 1px solid var(--vtYellow);
      margin-bottom: 0.4rem;
    }

    button {
      margin-bottom: 0.4rem;
      margin-right: 0.6rem;
      margin-left: auto;
      border-radius: 0.4rem;

      width: 0.8rem;
    }

    button > span {
      display: none;
    }

    h3 {
      position: relative;
    }

    h3::after {
      position: absolute;
      content: "";
      display: block;
      width: 100%;
      height: 2px;
    }
  }

  @container card (max-width: 480px) {
    button {
      margin-bottom: 0.4rem;
      margin-right: 0.6rem;
      margin-left: auto;
      border-radius: 0.4rem;

      width: 0.8rem;
    }

    button > span:nth-child(2) {
      display: none;
    }
  }

  @container card (max-width: 420px) {

    button > span {
      display: none;
    }
  }
</style>

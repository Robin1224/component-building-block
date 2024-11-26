<script>
  export let bgColor = "--vtYellow";
  export let color = "#000";

  export let text = "";

  // If href is given, the button will be a link
  export let href = "";

  export let className = "";
</script>

<!-- Check if it's a link or not. If it is, render an <a> instead of an <button> -->
{#if href}
  <a {href} style="--bg: var({bgColor}); --color: {color}" class={className}>
    {#if text}
      <span>{text}</span>
    {/if}
    <slot></slot>
  </a>
{:else}
  <button style="--bg: var({bgColor}); --color: {color}" class={className}>
    {#if text}
      <span>{text}</span>
    {/if}
    <slot></slot>
  </button>
{/if}

<style>
  a,
  button {
    background-color: var(--bg);
    color: var(--color);
    padding: 0.4rem 0.8rem;
    cursor: pointer;
    border-radius: 3px;
    border: none;
    height: fit-content;
    min-width: fit-content;
    max-width: 12rem;
  }

  span {
    font-family: var(--vtPrimaryFont);
    color: var(--vtDarkBlue);
    font-size: 1rem;
    font-weight: 400;
    margin-right: 0.2rem;
  }

  a :global(.icon-arrows), button :global(.icon-arrows) {
    transform: translateY(1px) translateX(1px);
    height: 0.8rem;
    width: auto;
  }

</style>

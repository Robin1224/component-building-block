<script>
  export let bgColor = "--vtYellow";
  export let color = "#000";

  // If href is given, the button will be a link
  export let href = "";

  export let className = "";
</script>

<!-- Check if it's a link or not. If it is, render an <a> instead of an <button> -->
{#if href}
  <a {href} style="--bg: var({bgColor}); --color: {color}" class={className}>
    <slot></slot>
  </a>
{:else}
  <button style="--bg: var({bgColor}); --color: {color}" class={className}>
    <slot></slot>
  </button>
{/if}

<style>
  a, button {
    background-color: var(--bg);
    color: var(--color);
    padding: 0.4rem;
    cursor: pointer;
    border-radius: 3px;
    border: none;
    height: fit-content;
    width: fit-content;
  }
</style>
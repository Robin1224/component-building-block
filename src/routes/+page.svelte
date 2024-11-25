<script>
  import CardsList from "$lib/molecules/CardsList.svelte";

  export let data;

  const {page, methods} = data;
</script>

<CardsList data={methods}/>

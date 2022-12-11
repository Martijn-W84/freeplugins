<script>
    export let plugins;
    export let filterTerm;
    export let searchTerm;

    import Card from "./Card.svelte";
</script>

<ul class="link-card-grid">
	{#each plugins as plugin }
		<Card {plugin} show={(plugin.category === filterTerm || filterTerm.toUpperCase() === "ALL") && (plugin.name.toUpperCase().includes(searchTerm.toUpperCase()) || plugin.developer.toUpperCase().includes(searchTerm.toUpperCase()) || plugin.category.toUpperCase().includes(searchTerm.toUpperCase()))}></Card>
	{/each}
</ul>

<style>
    .link-card-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(32ch, 1fr));
		gap: 1rem;
		padding: 0;
	}

	@media (min-width: 600px) {
  		.link-card-grid { grid-template-columns: repeat(2, 1fr); grid-template-rows: masonry;}
	}

	@media (min-width: 900px) {
  		.link-card-grid { grid-template-columns: repeat(3, 1fr); grid-template-rows: masonry;}
	}
</style>
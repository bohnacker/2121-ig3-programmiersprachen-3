<script>
	import { fly } from 'svelte/transition';
	let items = [
		{ id: 1, text: 'Oranges' },
		{ id: 2, text: 'Apples' },
		{ id: 3, text: 'Bananas' },
		{ id: 4, text: 'Pears' },
	];

	function handleItemClick(i) {
		console.log(i);
		items.splice(i, 1);
		items = items;
	}
</script>

{#each items as item, index (item.id)}
	<div class="item" on:click={() => handleItemClick(index)} transition:fly={{ x: 50, duration: 2000 }}>{item.text}</div>
{/each}

<style>
	.item {
		padding: 5px;
		user-select: none;
	}
</style>

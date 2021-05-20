<script>
	let todos = ['Learn Svelte', 'Make something cool', 'Pause', 'Weiterarbeiten'];

	let inputFocussed = false;
	let inputText = '';

	function handleNewItemClick() {
		if (inputText != '') {
			todos.push(inputText);
			todos = todos;
			inputText = '';
		}
	}

	function removeItem(index) {
		console.log(index);
		todos.splice(index, 1);
		todos = todos;
	}

	function handleInputFocus() {
		console.log('input got focus');
		inputFocussed = true;
	}
	function handleInputBlur() {
		console.log('input lost focus');
		inputFocussed = false;
	}
</script>

<main>
	<div id="container">
		<h2>Todos</h2>

		{#each todos as todo, index}
			<div class="item">
				{todo}
				<span class="remove-button" on:click={() => removeItem(index)}>Remove</span>
			</div>
		{/each}

		<input type="text" bind:value={inputText} on:focus={handleInputFocus} on:blur={handleInputBlur} />

		{#if inputText != '' || inputFocussed}
			<button on:click={handleNewItemClick}>Add new item</button>
		{/if}
	</div>
</main>

<style>
	#container {
		position: absolute;
		left: 200px;
		top: 100px;
		border: 1px solid black;
		padding: 10px;
		border-radius: 5px;
	}

	.item {
		padding: 10px 0px;
	}

	input {
		margin-top: 10px;
	}

	.remove-button {
		font-size: small;
		color: red;
		user-select: none;
	}
</style>

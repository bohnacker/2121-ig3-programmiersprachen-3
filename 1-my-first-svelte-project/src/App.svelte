<script>
	import jquery from "jquery";
	import Popup from './Popup.svelte';

	console.log();

	let todos = [
		{ text: 'Learn Svelte', done: false, label: 'red' },
		{ text: 'Make something cool', done: false },
		{ text: 'Carry on', done: false },
	];

	let inputFocussed = false;
	let inputText = '';

	let hoveredItem;

	let selectedItem = 1;

	function handleItemClick(index) {
		if (index != selectedItem) {
			selectedItem = index;
		} else {
			selectedItem = undefined;
		}
	}

	function handleNewItemClick() {
		if (inputText != '') {
			todos.push({ text: inputText, done: false });
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
		// console.log('input got focus');
		inputFocussed = true;
	}
	function handleInputBlur() {
		// console.log('input lost focus');
		inputFocussed = false;
	}

	function handleKeyup(event) {
		// console.log(event);
		if (event.key == 'Enter') {
			handleNewItemClick();
		}
	}
</script>

<main>
	<div id="container">
		<h2>Todos</h2>

		{#each todos as todo, index}
			<div class="item" on:mouseenter={() => (hoveredItem = index)} on:mouseleave={() => (hoveredItem = undefined)}>
				<div
					bind:this={todo.node}
					class="item-text"
					class:done={todo.done == true}
					style="color:{todo.label ?? 'black'}"
					on:click={() => handleItemClick(index)}
				>
					{todo.text}
				</div>

				{#if hoveredItem == index}
					<div class="remove-button" on:click={() => removeItem(index)}>Remove</div>
				{/if}

				<!-- <span class="remove-button" on:click={() => removeItem(index)} style={hoveredItem == index ? "" : "display:none"}>Remove2</span> -->
			</div>
		{/each}

		<input type="text" bind:value={inputText} on:focus={handleInputFocus} on:blur={handleInputBlur} on:keyup={handleKeyup} />

		{#if inputText != '' || inputFocussed}
			<button on:click={handleNewItemClick}>Add</button>
		{/if}
	</div>

	{#if selectedItem >= 0}
		<Popup bind:item={todos[selectedItem]} bind:selectedItem />
	{/if}
</main>

<style>
	#container {
		position: absolute;
		left: 200px;
		top: 100px;
		width: 300px;
		border: 1px solid black;
		padding: 10px;
		border-radius: 5px;
	}

	/* Container */
	.item {
		display: flex;
		justify-content: space-between;
		align-items: baseline;
		padding: 10px 0px;
		user-select: none;
	}

	.item-text.done {
		text-decoration: line-through;
	}

	.remove-button {
		font-size: small;
		color: red;
		/* user-select: none; */
		/* float:right; */
	}

	input {
		margin-top: 10px;
	}
</style>

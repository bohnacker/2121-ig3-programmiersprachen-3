<script>

	let screen = 1;

	function handleButtonClick() {
		screen++;
		if (screen > 3) {
			screen = 1;
		}
	}
</script>

<button on:click={handleButtonClick}>Nächster Screen</button>



{#if screen == 1}
	<div>Das ist der Screen 1</div>
{/if}



{#if screen == 2}
	<h1>Das ist der Screen 2</h1>
	<button
		on:click={() => {
			screen = 1;
		}}>Geh zurück</button
	>
{/if}



{#if screen == 3}
	aöisdhf aöisuf haösuifh aösdiuhf öaiwueh laiuewhf laisdugf lajsdgf lajsdgf
{/if}



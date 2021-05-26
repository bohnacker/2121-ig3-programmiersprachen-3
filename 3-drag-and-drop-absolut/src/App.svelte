<script>
	let dragging = false;
	let offsetX, offsetY;
	let posX = 200;
	let posY = 100;

	function handleMouseDown(event) {
		// console.log(event);
		dragging = true;
		offsetX = event.clientX - posX;
		offsetY = event.clientY - posY;
		// posX = event.target.getBoundingClientRect().left;
		// posY = event.target.getBoundingClientRect().top;
	}

	function handleMouseMove(event) {
		// console.log(event);
		posX = event.clientX - offsetX;
		posY = event.clientY - offsetY;

		if (posX < 0) {
			posX = 0;
		}
		if (posY < 0) {
			posY = 0;
		}
	}

	function handleMouseUp(event) {
		// console.log(event);
		dragging = false;
	}

</script>

<svelte:window 
	on:mousemove={dragging ? handleMouseMove : ''} 
	on:mouseup={dragging ? handleMouseUp : ''} />

<div id="box" on:mousedown={handleMouseDown} style="left: {posX}px; top: {posY}px"/>

<style>
	#box {
		position: absolute;
		width: 150px;
		height: 150px;
		background-color: orangered;
	}
</style>

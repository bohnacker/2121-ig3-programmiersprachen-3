<script>
	let x = 100;
	let y = 100;
	
	function handleClick() {
		 x = Math.random() * (window.innerWidth - 100);
		 y = Math.random() * (window.innerHeight - 100);
	}

</script>


<div id="box" on:click={handleClick} style="left: {x}px; top: {y}px;">

</div>


<style>
	#box {
		position: absolute;
		width: 100px;
		height: 100px;
		background-color: orchid;
		transition: all 1s ease-in-out;
	}

</style>
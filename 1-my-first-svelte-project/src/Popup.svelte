<script>
  export let label;
  

</script>

<div id="popup">
  <button on:click={() => label = "red"}>1</button>
  <button on:click={() => label = "orange"}>2</button>
  <button on:click={() => label = "green"}>3</button>
  {label}
</div>

<style>
  #popup {
    width: 150px;
    height: 70px;
    background-color: #eee;
    border: 1px solid black;
    border-radius: 5px;
    padding: 5px;
  }

</style>
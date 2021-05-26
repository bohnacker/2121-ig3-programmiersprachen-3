<script>
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();
  
  export let item;
  let x, y;

  $: if (item.node) {
    let itemBounds = item.node.getBoundingClientRect();
    x = itemBounds.right + 20;
    y = itemBounds.top - 10;
  }
</script>

<div on:click|stopPropagation={() => {}} id="popup" style="left:{x}px; top:{y}px">
  <button on:click={() => (item.label = 'red')} style="background-color:red">1</button>
  <button on:click={() => (item.label = 'orange')} style="background-color:orange">2</button>
  <button on:click={() => (item.label = 'green')} style="background-color:green">3</button>
  <button on:click={() => (item.label = undefined)}>None</button>
</div>

<style>
  #popup {
    width: max-content;
    /* height: 70px; */
    background-color: #eee;
    border: 1px solid black;
    border-radius: 5px;
    padding: 5px;
    position: absolute;
  }

  button {
    min-width: 30px;
    height: 30px;
    padding: 0 5px;
    border-radius: 5px;
  }
</style>

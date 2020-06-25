<script>
  import { createEventDispatcher } from "svelte";

  let dispatch = createEventDispatcher();
  export let name;
  export let score;
  let showControls = false;

  const scorePlusOne = () => {
    score += 1;
  };

  const scoreMinusOne = () => {
    score -= 1;
  };
  const toggleControls = () => {
    showControls = !showControls;
  };
  const removePlayer = () => {
    dispatch("removePlayer", name);
  };
</script>

<style>
  h1 {
    color: #204f6e;
  }
  h3 {
    margin-bottom: 10px;
  }
</style>

<div class="card">
  <h1>
    {name}
    <button class="btn btn-sm" on:click={toggleControls}>
      {#if showControls}-{:else}+{/if}
    </button>
    <button class="btn btn-danger btn-sm" on:click={removePlayer}>X</button>
  </h1>
  <h3>Score: {score}</h3>
  {#if showControls}
    <button class="btn" on:click={scorePlusOne}>+1</button>
    <button class="btn btn-dark" on:click={scoreMinusOne}>-1</button>
    <input type="number" bind:value={score} />
  {/if}
</div>

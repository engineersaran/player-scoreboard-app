<script>
  import { createEventDispatcher } from "svelte";

  let dispatch = createEventDispatcher();

  let player = {
    name: "",
    score: 0
  };
  const addPlayer = event => {
    event.preventDefault();
    dispatch("addPlayer", player);
    player = {
      name: "",
      score: 0
    };
  };
</script>

<form on:submit={addPlayer} class="grid-3">
  <input
    type="text"
    placeholder="Player Name"
    bind:value={player.name}
    required />
  <input
    type="number"
    placeholder="Player Score"
    bind:value={player.score}
    required />
  <input type="submit" class="btn btn-primary" value="Add Player" />
</form>

<script>
  import NAVBAR from "./navbar.svelte";
  import PLAYER from "./player.svelte";
  import ADDPLAYER from "./addPlayer.svelte";

  let players = [
    {
      name: "Saravanakumar Ramalingam",
      score: 53
    },
    {
      name: "Vincent Woo",
      score: 45
    },
    {
      name: "Tony Jun",
      score: 34
    }
  ];
  const addPlayer = event => {
    const newPlayer = event.detail;
    players = [...players, newPlayer];
  };

  const removePlayer = event => {
    const playerName = event.detail;
    players = players.filter(player => player.name !== playerName);
  };
</script>

<style>

</style>

<NAVBAR />
<div class="container">
  <ADDPLAYER on:addPlayer={addPlayer} />
  {#if players.length === 0}
    <p>No Players</p>
  {:else}
    {#each players as player}
      <PLAYER
        name={player.name}
        score={player.score}
        on:removePlayer={removePlayer} />
    {/each}
  {/if}
</div>

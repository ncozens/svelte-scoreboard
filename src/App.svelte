<script>
  import Navbar from "./Navbar.svelte";
  import Player from "./Player.svelte";
  import AddPlayer from "./AddPlayer.svelte";

  let players = [
    {
      name: "John Doe",
      points: 21
    },
    {
      name: "Corey Taylor",
      points: 36
    },
    {
      name: "Mike Herrera",
      points: 18
    }
  ];

  const addPlayer = e => {
    const newPlayer = e.detail;
    players = [...players, newPlayer];
  };

  const removePlayer = e => {
	  players = players.filter(player => player.name !== e.detail);
  };
</script>

<Navbar />
<div class="container">
  <AddPlayer on:addplayer={addPlayer} />
  {#if players.length === 0}
    <p>There aren't any players... please add some.</p>
  {:else}
    {#each players as player}
      <Player name={player.name} points={player.points} on:deleteplayer={removePlayer}/>
    {/each}
  {/if}
</div>

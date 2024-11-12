<script>
  import Team from "./lib/Team.svelte";

  let redHp = 20;
  let blueHp = 20;
  // let winningText = "";

  $: redWon = blueHp === 0;
  $: blueWon = redHp === 0;
  $: gameOver = redWon || blueWon;
  // $: if (blueWon) {
  //   winningText = "Blue Won!";
  // } else {
  //   winningText = "Red Won!";
  // }

  function resetGame() {
    redHp = 20;
    blueHp = 20;
  }
</script>

<div class="row mt-2">
  <div class="col">
    <h2 class="text-center">MTG Counter App</h2>
  </div>
</div>

<div class="row">
  <Team teamName="Red" bind:health={redHp} {gameOver} />
  <Team teamName="Blue" bind:health={blueHp} {gameOver} />
</div>

{#if !gameOver}
  <div class="row mt-3">
    <div class="col">
      <button class="btn btn-warning w-100" on:click={resetGame}
        >Reset Game</button
      >
    </div>
  </div>
{:else}
  <div class="row mt-3">
    <div class="col">
      {#if blueWon}
        <h2 class="text-center text-primary">Blue Won!</h2>
      {:else}
        <h2 class="text-center text-danger">Red Won!</h2>
      {/if}
      <button class="btn btn-success w-100" on:click={resetGame}
        >New Game</button
      >
    </div>
  </div>
{/if}

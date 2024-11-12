<script>
    export let teamName = "";
    export let health;
    export let gameOver;

    function incrementHealth() {
        health = health + 1;
    }

    function decrementHealth() {
        health = health - 1;
    }
</script>

<div
    class="col"
    style="border: dashed {teamName.toLowerCase()} 5px"
    id="health-{teamName}"
>
    <h2
        class:text-danger={teamName.toLowerCase() === "red"}
        class:text-primary={teamName.toLowerCase() === "blue"}
    >
        Team {teamName}: {health}
    </h2>
    <button
        disabled={gameOver}
        class="btn btn-success"
        on:click={incrementHealth}>+</button
    >
    <button
        disabled={gameOver}
        class="btn btn-danger"
        on:click={decrementHealth}>-</button
    >
</div>

<style>
    div.col {
        padding: 20px;
        text-align: center;
    }
</style>

<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();
    export let name = "rohan";
    export let points = 100;
    let showControls = true;
    const toggle = () => (showControls = !showControls);
    const addPoints = () => (points += 1);
    const removePoints = () => (points -= 1);
    const onDelete = () => {
        dispatch("removeplayer", name);
    };
</script>

<div class="card">
    <h1>
        {name}
        <button class="btn btn-success" on:click={toggle}>Toggle</button>
        <button class="btn btn-danger" on:click={onDelete}>Delete</button>
    </h1>
    <p>Points: {points}</p>
    {#if showControls}
        <button class="btn btn-dark" on:click={addPoints}>+1</button>
        <button class="btn btn-primary" on:click={removePoints}>-1</button>
        <input type="number" name="" id="" bind:value={points} />
    {/if}
</div>

<style>
    h1 {
        color: #ff3e00;
        text-transform: uppercase;
        font-size: 4em;
        font-weight: 100;
    }
    p {
        margin-bottom: 10px;
    }
</style>

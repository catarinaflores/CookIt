<script>
    import CutSausage from '$lib/cutSausage.svelte'
    import PanSausage from '$lib/panSausage.svelte';
    import CrackEgg from '$lib/crackEgg.svelte';
    import FlipOmelette from '$lib/flipOmelette.svelte';
    import Recepies from '$lib/recepies.svelte';

    let cookingStation = CrackEgg;

    function showCutSausage() {
        cookingStation = CutSausage;
    }

    function showCrackEgg() {
        cookingStation = CrackEgg;
    }

    function showFlipOmelette() {
        cookingStation = FlipOmelette;
    }

    function showPanSausage() {
        cookingStation = PanSausage;
    }


</script>

<main>
    <header>
        <img src="/logo.svg" alt="CookIt" />
    </header>

    <div class=choices>
        <button on:click={showCrackEgg}>Crack the Eggs</button>
        <button on:click={showCutSausage}>Cut the Sausage</button>
        <button on:click={showPanSausage}>Place Sausage in Pan</button>
        <button on:click={showFlipOmelette}>Flip the Omelette</button>
    </div>

    <!-- Render dynamic component -->
    <svelte:component this={cookingStation} />

    <!-- <div class="choices">
        <button on:click={showCrackEgg}>Previous</button>
        <button on:click={showPanSausage}>Next</button>
    </div> -->

    <!-- Static component -->
    <Recepies />
</main>

<style>
    header{
        justify-content: center;
        display: flex;
        align-items: center;
        background-color: black;
    }

    
    main{
        background-color: aqua;
    }

    .choices{
        display: flex;
        justify-content: center;
        align-items: center;
        margin-top: 40px;
        gap: 20px;
        flex-wrap: wrap;
    }
</style>
<script>
    import CookingStation from '$lib/cookingStation.svelte';
</script>

<main>
    <header>
        <h1>CookIt</h1>
    </header>

    <CookingStation />
</main>

<style>
    header{
        justify-content: center;
        display: flex;
        align-items: center;
        background-color: black;
    }

    header h1{
        color: white;
    }
    
    main{
        background-color: aqua;
    }
</style>
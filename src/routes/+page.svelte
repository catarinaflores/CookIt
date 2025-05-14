<script>
    import CutSausage from '$lib/cutSausage.svelte'
    import cutSausage from '$lib/cutSausage.svelte';
    import Recepies from '$lib/recepies.svelte';
</script>

<main>
    <header>
        <img src="/logo.svg" alt="CookIt" />
    </header>

    <div class=choices>
        <button>Crack the Eggs</button>
        <button>Cut the Sausage</button>
        <button>Place Sausage in Pan</button>
        <button>Cook the Omelette</button>
    </div>

    <CutSausage />
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
</style>
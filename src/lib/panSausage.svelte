<script>
    import { onMount } from 'svelte';

    let slices = []; // Array to store the positions of the spawned slices

    function handlePanClick(event) {
        const pan = event.currentTarget; // The clicked element (pan image)
        const rect = pan.getBoundingClientRect(); // Get the bounding box of the pan

        // Calculate the position of the click relative to the pan
        const x = event.clientX - rect.left;
        const y = event.clientY - rect.top;

        // Add the new slice position to the array
        slices = [...slices, { x, y }];
    }
</script>

<div id="pan-sausage">
    <div id="pan" on:click={handlePanClick}>
        <img src="panela.svg" alt="pan" />
        {#each slices as slice (slice)}
            <img
                src="rodela.svg"
                class="slice"
                style="left: {slice.x}px; top: {slice.y}px;"
                alt="slice"
            />
        {/each}
    </div>
</div>

<style global>
    #pan-sausage {
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: red;
        height: 85vh;
        width: 85vw;
        margin: 7% auto;
        position: relative;
    }

    #pan {
        width: 100%;
        height: 100%;
        z-index: 1;
        position: relative;
    }

    #pan img {
        height: 100%;
        width: 100%;
        object-fit: contain;
        display: block;
    }

    .slice {
        position: absolute;
        width: 10px; /* Adjust size as needed */
        height: 10px; /* Adjust size as needed */
        transform: translate(-50%, -50%); /* Center the slice on the click */
    }
</style>
<script>
    import { draw } from 'svelte/transition';
    import { quintOut } from 'svelte/easing';

    let crack = 0;
    let bouncing = false;

    function handleCrack() {
        // Bounce trigger
        bouncing = true;
        setTimeout(() => bouncing = false, 300); // match animation duration

        // Crack logic
        crack += 1;
        if (crack > 3) {
            crack = 0;
        }
    }
</script>

<div id="container">
    <div class="egg {bouncing ? 'bouncing' : ''}" on:click={handleCrack}>
        <svg width="108" height="144" viewBox="0 0 108 144" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M54 143.061C98.5635 142.703 110.294 103.218 107.648 71.5305C105.073 40.4862 79.3933 0.286122 54 0C28.6067 0.286122 2.92724 40.4862 0.352146 71.5305C-2.29448 103.218 9.43651 142.703 54 143.061Z" fill="#FCDBBE"/>
            
            {#if crack >= 1}
                <path transition:draw="{{ duration: 500, easing: quintOut }}" d="M13.0489 31.5529L24.0489 44.5529M24.0489 44.5529L22.6672 54.8759L25.1672 56.8759L24.0489 60.8759M24.0489 44.5529L29.6672 45.8759L37.6672 40.3759L41.6672 44.8759" stroke="#D18C4F"/>
            {/if}
            {#if crack >= 2}
                <path transition:draw="{{ duration: 500, easing: quintOut }}" d="M106.221 58.505L91.4239 75.9921M91.4239 75.9921L93.2825 89.8781L89.9196 92.5685L91.4239 97.9491M91.4239 75.9921L83.8664 77.7717L73.1051 70.3733L67.7245 76.4265" stroke="#D18C4F" stroke-width="1.34516"/>
            {/if}
            {#if crack >= 3}
                <path transition:draw="{{ duration: 500, easing: quintOut }}" d="M22.5006 134.975L23.5006 114.975L37 110.5L37 96.5L43.5 96.5L45 92.5" stroke="#D18C4F"/>
            {/if}
        </svg>
    </div>
</div>

<style>
    #container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        height: 85vh;
        width: 85vw;
        margin: 7% auto;
        background-color: white;
        overflow: hidden;
        border-radius: 30px;
    }

    .egg {
        width: 40%;
        max-width: 300px;
        cursor: pointer;
    }

    .egg svg {
        width: 100%;
        height: auto;
        display: block;
    }

    .bouncing {
        animation: bounce 0.3s ease;
    }

    @keyframes bounce {
        0%   { transform: translateX(0); }
        30%  { transform: translateX(-10px); }
        60%  { transform: translateX(5px); }
        100% { transform: translateX(0); }
    }

    @media (max-width: 800px) {
        #container {
            height: 50vh;
            border-radius: 20px;
        }

        .egg {
            width: 60%;
        }
    }
</style>

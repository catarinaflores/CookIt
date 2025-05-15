<script>
    import PanSausage from "./panSausage.svelte";
	import {draw} from 'svelte/transition';
	import { quintOut } from 'svelte/easing';

	let bgColor = "yellow";
	let slices = 0;

	function handleKnifeClick(){
		slices += 1;
		if (slices > 7) {
			slices = 7;
		}
	}

</script>

<div id="container" style="background-color: {bgColor};">
	<div class="sausage">
		<svg width="298" height="63" viewBox="0 0 298 63" fill="none" xmlns="http://www.w3.org/2000/svg">
			<rect x="13" y="11" width="271" height="44" rx="22" fill="#D58E6F"/>
			<path d="M281.126 32.1677L292.912 23.3855L293.13 40.6484L281.126 32.1677Z" fill="#D58E6F"/>
			<path d="M15.9858 32.1677L4.20058 23.3855L3.98178 40.6484L15.9858 32.1677Z" fill="#D58E6F"/>
			{#if slices >= 1}
				<line transition:draw="{{duration: 1500, easing: quintOut}}" x1="41.5" y1="1.09278e-07" x2="41.5" y2="63" stroke={bgColor} stroke-width="5"/>
			{/if}
			{#if slices >= 2}
				<line transition:draw="{{duration: 1500, easing: quintOut}}" x1="76.5" y1="1.09278e-07" x2="76.5" y2="63" stroke={bgColor} stroke-width="5"/>
			{/if}
			{#if slices >= 3}
				<line transition:draw="{{duration: 1500, easing: quintOut}}" x1="111.5" y1="1.09278e-07" x2="111.5" y2="63" stroke={bgColor} stroke-width="5"/>
			{/if}
			{#if slices >= 4}
				<line transition:draw="{{duration: 1500, easing: quintOut}}" x1="146.5" y1="1.09278e-07" x2="146.5" y2="63" stroke={bgColor} stroke-width="5"/>
			{/if}
			{#if slices >= 5}
				<line transition:draw="{{duration: 1500, easing: quintOut}}" x1="181.5" y1="1.09278e-07" x2="181.5" y2="63" stroke={bgColor} stroke-width="5"/>
			{/if}
			{#if slices >= 6}
				<line transition:draw="{{duration: 1500, easing: quintOut}}" x1="216.5" y1="1.09278e-07" x2="216.5" y2="63" stroke={bgColor} stroke-width="5"/>
			{/if}
			{#if slices == 7}
				<line transition:draw="{{duration: 1500, easing: quintOut}}" x1="251.5" y1="1.09278e-07" x2="251.5" y2="63" stroke={bgColor} stroke-width="5"/>
			{/if}
		</svg>
	</div>

	<h1>{slices} Slices</h1>

	<button aria-label="Cut sausage with knife" class="knife-button" on:click={handleKnifeClick}>
		<svg width="523" height="81" viewBox="0 0 523 81" fill="none" xmlns="http://www.w3.org/2000/svg">
			<g clip-path="url(#clip0_127_52)">
				<path d="M409.931 62.5843C402.441 64.1687 394.735 65.6811 386.813 67.1214C375.29 69.21 363.262 71.1545 350.947 72.8829C332.366 75.4756 312.921 77.5642 292.972 78.8605C266.109 80.661 238.31 81.0931 210.583 79.5087C198.628 78.8605 210.151 47.1723 188.761 36.7295C187.897 36.2974 187.105 35.7933 186.24 35.1451C178.967 29.6717 171.837 16.6363 177.382 7.56196C177.742 6.91379 181.271 6.33764 187.321 5.83351C210.439 3.88901 270.79 2.88074 334.815 4.60919C352.532 5.11333 370.608 5.76149 388.181 6.69774C398.912 7.27389 409.426 7.92206 419.725 8.71426C426.423 9.21839 432.977 9.79454 439.386 10.3707C475.9 13.7556 506.436 18.5808 522.424 25.3506C528.978 28.2313 481.373 47.6044 409.931 62.5843Z" fill="#CCCCCC"/>
				<path d="M14.1157 1.6451e-05L182.207 3.45692C185.808 3.52893 188.689 6.4817 188.689 10.0826V29.9598C188.689 33.7048 185.592 36.6575 181.919 36.5855L42.203 33.5607C41.9149 33.5607 41.6268 33.5607 41.3388 33.4887C39.6823 33.2727 32.9126 32.7685 28.5194 39.8984C24.7744 46.236 9.29042 33.1286 2.16056 26.5749C1.08451e-06 24.5584 -0.576149 21.3896 0.720188 18.7249L8.0661 3.74499C9.14638 1.36837 11.595 -0.0720023 14.1157 1.6451e-05Z" fill="#BA8350"/>
				<path d="M113.862 23.6221C117.044 23.6221 119.623 21.0426 119.623 17.8606C119.623 14.6786 117.044 12.0991 113.862 12.0991C110.68 12.0991 108.1 14.6786 108.1 17.8606C108.1 21.0426 110.68 23.6221 113.862 23.6221Z" fill="#CCCCCC"/>
				<path d="M26.7189 22.1817C29.9009 22.1817 32.4804 19.6022 32.4804 16.4203C32.4804 13.2383 29.9009 10.6588 26.7189 10.6588C23.537 10.6588 20.9575 13.2383 20.9575 16.4203C20.9575 19.6022 23.537 22.1817 26.7189 22.1817Z" fill="#CCCCCC"/>
				<path d="M388.181 6.76975L350.947 72.8829C332.366 75.4756 312.921 77.5642 292.972 78.8605L334.815 4.60919C352.532 5.11332 370.608 5.83351 388.181 6.76975Z" fill="#DDDDDD"/>
				<path d="M439.314 10.3707L409.931 62.5843C402.441 64.1687 394.735 65.6811 386.813 67.1215L419.725 8.78632C426.423 9.29045 432.977 9.79458 439.314 10.3707Z" fill="#DDDDDD"/>
			</g>
			<defs>
				<clipPath id="clip0_127_52">
					<rect width="523" height="80.5169" fill="white"/>
				</clipPath>
			</defs>
		</svg>
	</button>


</div>

<style global>
	#container {
		justify-content: space-between;
		flex-direction: column;
		height: 100vh;
		display: flex;
		height: 85vh;
		width: 85vw;
		margin: 7% auto;
	}

    #container .sausage {
		align-self: center;
		margin-top: 20%;
		width: 100%;
    }
	.sausage svg{
		width: 100%;
		height: 100%;
		object-fit: contain;
	}

	#container .knife-button{
		justify-content: flex-end;
		margin-bottom: 5%;
		margin-right: 20%;
		margin-left: 20%;
	}

	.knife-button svg{
		width: 100%;
		height: 100%;
		object-fit: contain;
	}
</style>
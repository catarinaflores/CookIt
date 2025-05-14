<script>
    import PanSausage from "./panSausage.svelte";

	let knife;
    let sausage;
	let isDragging = false;
	let offsetX, offsetY;

	// Mouse Events

	function handleMouseDown(event) {
		event.preventDefault();
		isDragging = true;

		const rect = knife.getBoundingClientRect();
		offsetX = event.clientX - rect.left;
		offsetY = event.clientY - rect.top;

		window.addEventListener('mousemove', handleMouseMove);
		window.addEventListener('mouseup', handleMouseUp);
	}

	function handleMouseMove(event) {
		if (!isDragging) return;

		moveKnife(event.clientX, event.clientY);
	}

	function handleMouseUp() {
		isDragging = false;
		window.removeEventListener('mousemove', handleMouseMove);
		window.removeEventListener('mouseup', handleMouseUp);
	}

	// --- Touch Events ---

	/* function handleTouchStart(event) {
		event.preventDefault();

		const rect = knife.getBoundingClientRect();
		offsetX = event.touches[0].clientX - rect.left;
		offsetY = event.touches[0].clientY - rect.top;

		window.addEventListener('touchmove', handleTouchMove);
		window.addEventListener('touchend', handleTouchEnd);
	}

	function handleTouchMove(event) {
		if (!isDragging) return;

		moveKnife(event.touches[0].clientX, event.touches[0].clientY);
	}

	function handleTouchEnd() {
		isDragging = false;
		window.removeEventListener('touchmove', handleTouchMove);
		window.removeEventListener('touchend', handleTouchEnd);
	}
    */
	// --- Core Functions ---

	function moveKnife(clientX, clientY) {
		const container = document.getElementById('cutting-sausage');
		const containerRect = container.getBoundingClientRect();

		let x = clientX - containerRect.left - offsetX;
		let y = clientY - containerRect.top - offsetY;

		const maxX = container.clientWidth - knife.clientWidth;
		const maxY = container.clientHeight - knife.clientHeight;

		x = Math.max(0, Math.min(x, maxX));
		y = Math.max(0, Math.min(y, maxY));

		knife.style.left = `${x}px`;
		knife.style.top = `${y}px`;
	}

</script>

<div id="cutting-sausage">
	<!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
	<img
		bind:this={knife}
		src="/knife.svg"
		class="draggable"
		on:mousedown={handleMouseDown}
		alt="knife"
		draggable="false"
	/>
    <img
        bind:this={sausage}
        src="/sausage.svg" alt="sausage" id="sausage"/>
</div>

<style global>
	#cutting-sausage {
		display: flex;
		justify-content: center;
		align-items: center;
		background-color: yellow;
		height: 85vh;
		width: 85vw;
		margin: 7% auto;
		position: relative;
        overflow: hidden;
	}

    #sausage {
        position: absolute;
        width: 50%;
        height: 50%;
        z-index: 1;
        transform: rotate(90deg);
    }
    
	.draggable {
		position: absolute;
		width: 40%;
		height: 40%;
		cursor: grab;
		z-index: 2;
		user-select: none;
		touch-action: none;
	}


	@media (max-width: 768px) {
		#cutting-sausage {
			height: 65vh;
		}
	}

	@media (max-width: 480px) {
		#cutting-sausage {
			height: 30vh;
		}
	}


	.draggable:active {
		cursor: grabbing;
	}


</style>
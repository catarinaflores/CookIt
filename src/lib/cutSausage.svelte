<script>
    let knife;
    let offsetX, offsetY;
    let isDragging = false;

    // Mouse movement

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

    const container = document.getElementById('cutting-sausage');
    const containerRect = container.getBoundingClientRect();

    let x = event.clientX - containerRect.left - offsetX;
    let y = event.clientY - containerRect.top - offsetY;


    // Clamp to stay inside container
    const maxX = container.clientWidth - knife.clientWidth;
    const maxY = container.clientHeight - knife.clientHeight;

    x = Math.max(0, Math.min(x, maxX));
    y = Math.max(0, Math.min(y, maxY));

    knife.style.left = `${x}px`;
    knife.style.top = `${y}px`;
  }

  function handleMouseUp() {
    isDragging = false;
    window.removeEventListener('mousemove', handleMouseMove);
    window.removeEventListener('mouseup', handleMouseUp);
  }

  // Touch movement
    function handleTouchStart(event) {
        event.preventDefault();
        isDragging = true;
    
        const rect = knife.getBoundingClientRect();
        offsetX = event.touches[0].clientX - rect.left;
        offsetY = event.touches[0].clientY - rect.top;
    
        window.addEventListener('touchmove', handleTouchMove);
        window.addEventListener('touchend', handleTouchEnd);
    }

    function handleTouchMove(event) {
        if (!isDragging) return;
    
        const container = document.getElementById('cutting-sausage');
        const containerRect = container.getBoundingClientRect();
    
        let x = event.touches[0].clientX - containerRect.left - offsetX;
        let y = event.touches[0].clientY - containerRect.top - offsetY;
    
        // Clamp to stay inside container
        const maxX = container.clientWidth - knife.clientWidth;
        const maxY = container.clientHeight - knife.clientHeight;
    
        x = Math.max(0, Math.min(x, maxX));
        y = Math.max(0, Math.min(y, maxY));
    
        knife.style.left = `${x}px`;
        knife.style.top = `${y}px`;
    }

    function handleTouchEnd() {
        isDragging = false;
        window.removeEventListener('touchmove', handleTouchMove);
        window.removeEventListener('touchend', handleTouchEnd);
    }
</script>


<div id="cutting-sausage">
    <img bind:this={knife} src="/knife.svg" class="draggable" on:mousedown={handleMouseDown} alt="knife" />

    <img src="/sasixa.svg" class="cuttable" alt="sausage"/>
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
    }


    @media (max-width: 768px){
        #cutting-sausage {
            height: 65vh;
        }
    }

    @media (max-width:480px){
        #cutting-sausage {
            height: 30vh;
        }
    }

    .draggable {
        position: absolute;
        width: 30%;
        height: 30%;
        cursor: grab;
        z-index: 2;
        user-select: none;
    }

    .draggable:active {
        cursor: grabbing;
    }

    .cuttable {
        width: 50%;
        height: 50%;
        z-index: 1;
        user-select: none;
    }
</style>

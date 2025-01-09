<script>    
    let isCollapsed = $state(true);
    let startY = $state(0);
    let currentY = $state(0);
    let updatedY = $derived(currentY - startY);
    let container;

    // Set default reference value
    const handleTouchStart = (event) => {
        startY = event.touches[0].clientY;
    };
    
    const handleTouchMove = (event) => {
        currentY = event.touches[0].clientY;

        // larger number it is, more collapsed it is
        if (updatedY > 0) {            
            // If the current clientY is larger (more to bottom) than the initial clientY and not isCollapsed
            container.style.height = innerHeight - updatedY + "px";
        } else if (updatedY < 0) {
            // If the current clientY is smaller than the initial clientY and isCollapsed
            container.style.height = - updatedY >= innerHeight ? "100vh"  : - updatedY + "px";
        }
    };
    
    const handleTouchEnd = () => {
        if (currentY > (innerHeight / 2)) {
            collapse();
        } else if (currentY < (innerHeight / 2)) {
            open();
        } else {
            isCollapsed ? open() : collapse();
        }
    };
    
    const collapse = () => {
        container.style.height = "5vh";
        isCollapsed = true;
    };
    
    const open = () => {
        container.style.height = "100vh";
        isCollapsed = false;
    };
    
    
</script>

<style>
    .container {
        position: fixed;
        bottom: 0;
        left: 0;
        right: 0;
        height: 5vh;
        background-color: #f8f9fa;
        border-top: 1px solid #dee2e6;
        transition: transform 0.3s ease;
        color: black;
        border-radius: 10px 10px 0 0;
    }
    .content {
         display: grid;
         place-items: center;
         padding-block: 1em;
    }
    .hr_line {
        width: 50%;
        height: 2px;
        background: gray;
    }
</style>

<div
    bind:this={container}
    class="container"
    on:touchstart={handleTouchStart}
    on:touchmove={handleTouchMove}
    on:touchend={handleTouchEnd}
>
    <div class="content">
        <div class="hr_line"></div>
    </div>
</div>
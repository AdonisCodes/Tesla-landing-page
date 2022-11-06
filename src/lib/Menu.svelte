<script>
// @ts-nocheck
    import { fade, blur, fly, slide, scale } from "svelte/transition";
    import { createEventDispatcher } from 'svelte'

    let EventDispatcher = createEventDispatcher()
    let menuItem = ['Existing Inventory', 'Used Inventory', 'Trade-In', 'Test Drive', 'Insurance', 'CyberTruck', 'Roadster', 'Semi', 'Charging', 'PowerWall', 'Commercial Energy', 'Utilities', 'Find Us', 'Support', 'Investor Relations']
    function handleMenuClose() {
        EventDispatcher('menuClosed')
    }

</script>

<div class="div" transition:fly="{{ x: 200, duration: 200 }}" >
    <div class="close-btn">
        <span on:mousedown={() => {handleMenuClose()}} class="material-symbols-outlined x-class">
            close
        </span>
    </div>
    <div class="x">
        <p class="p hover">hi</p>
    </div><div class="x" style="padding: 0.1vh 0.1vh;">
        <p class=" hover"></p>
    </div>
    
    {#each menuItem as item}
    <div class="x hover">
        <!-- svelte-ignore security-anchor-rel-noreferrer -->
        <a style="color: rgb(23, 26, 32);" href="https://www.youtube.com/watch?v=dQw4w9WgXcQ" target="_blank"><p class="">{item}</p></a>
    </div>
    {/each}
    
</div>

<style>

    .p {
        color: rgb(23, 26, 32);
    }

    .div {
        position: absolute;
        display: grid;
        grid-template-rows: auto;
        row-gap: 1vh;
        right: 0;
        top: 0;
        background-color: rgb(255, 255, 255);
        width: 40vh;
        overflow-y: scroll;
        height: 100vh;
        color: rgb(23, 26, 32);
    }

    .x {
        font-weight: bolder;
        display: flex;
        align-items: center;
        padding: 1vh 1vh;
        margin-left: 6vh;
        font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        width: 28vh;
    }

    .close-btn {
        color: rgb(23, 26, 32);
        font-weight: bolder;
        display: flex;
        align-items: center;
        right: 1vh;
        padding: 3vh 0vh;
        position: fixed;
        z-index: 150;
        width: 35vh;
        padding-right: 3vh;
        backface-visibility: hidden;
        background: inherit;

    }

    .x-class {
        margin-left: auto;
        font-size: 5vh;
        cursor: pointer;
        
    }

    @media (orientation: portrait) {
        .div {
            width: 42vh;
        }

        .close-btn {
            width: 37vh;
        }
    }


</style>
<script context="module">
    import Viewport from 'svelte-viewport-info'
    import Menu from "./Menu.svelte";
    import { createEventDispatcher } from 'svelte'
</script>

<script>
    let EventDispathcer = createEventDispatcher() 
    let orientation = Viewport.Orientation
    let menu = false
    function orientationHandler() {
        orientation = Viewport.Orientation
        console.log(orientation)
    }
    orientationHandler()
</script>
  
  <svelte:body on:orientationchangeend={() => orientationHandler()}/>

    <div class="nav">
        <div class="logo">
            <h1>TESLA</h1>
        </div>

        {#if orientation == 'landscape'}
        <div class="NavItem" >
            <h2>shop</h2>
            <h2>account</h2>
            <h2 on:mousedown={() => menu = !menu}>menu</h2>
        </div>
        {:else}
        <div on:mousedown={() => menu = !menu}  class="menu material-symbols-outlined">
            menu
        </div>
        {/if}

        {#if menu}
        <Menu on:menuClosed={() => menu = !menu} />
        {/if}

    </div>
<style>
    .nav {
        position: fixed;
        padding: 0 0;
        display: grid;
        grid-template-columns: 15fr 10fr;
        flex-direction: column;
        width: 100%;
        justify-content: center;
        align-items: center;
        vertical-align: middle;
        text-align: center;
        z-index: 100;
    }

    .logo {
        margin-right: auto ;
        margin-left: 1vh;
        margin-top: 1vh;
    }

    .NavItem {
        margin-top: 1vh;
        margin-bottom: 1vh;
        margin-left: auto;
        margin-right: 2vh;
        font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        font-weight: bold;

    }

    h1, h2 {
        display: inline;
        margin: 1vh 3vh;
        cursor: pointer;
        color: rgb(23, 26, 32);
    }

    .menu {
        margin-right: 3vh;
        text-align: right;
    }
</style>
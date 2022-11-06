<script context="module">
    import Viewport from 'svelte-viewport-info'
    import { createEventDispatcher } from 'svelte'
</script>

<script>
    let EventDispathcer = createEventDispatcher() 
    let orientation = Viewport.Orientation
    let menu = false
    let PCimages = [{img: 'M3-Homepage-Desktop-LHD.jfif', text1: 'Model 3', text2: ' Order Online for Touchless Deliver'}, {img: '/Homepage-SolarRoof-Desktop-Global.jfif', text1: 'Solar Roof', text2: ' Produce Clean Energy From Your Roof'}, {img: '/Homepage-Model-S-Desktop-LHD.jfif', text1: 'Model S', text2: 'Order Online for Touchless Delivery'} , {img: '/Desktop-ModelY.jfif', text1: 'Model X', text2: 'Order Online for Touchless Delivery'},{img: '/_25-HP-SolarPanels-D.jfif', text1: 'Solar Panels', text2: 'Order Online for Touchless Delivery'}]
    let Mimages = [{img: '/wp4998027.jpg', text1: 'Model 3', text2: ' Order Online for Touchless Deliver'}, {img: '/640189.jpg', text1: 'Solar Roof', text2: ' Produce Clean Energy From Your Roof'}, {img: '/ThB0xU.jpg', text1: 'Model S', text2: 'Order Online for Touchless Delivery'} , {img: '/795410.webp', text1: 'Model X', text2: 'Order Online for Touchless Delivery'},{img: '/9cf22c2eb8832980b5e7faea3dcb0a3a.jpg', text1: 'Solar Panels', text2: 'Order Online for Touchless Delivery'}]
    function orientationHandler() {
        orientation = Viewport.Orientation
        console.log(orientation)
    }
    orientationHandler()
</script>
  
  <svelte:body on:orientationchangeend={() => orientationHandler()}/>

<div class="div">

    {#if orientation == 'landscape'}
    {#each PCimages as image}
    <div style="background: url({image.img});height: 100vh;width: 100vw;background-size: 100vw 110vh;background-position: center;scroll-snap-align: start;" class="textAlign">
        <div class="infoDiv">
            <h1>{image.text1}</h1>
            <p>{image.text2}</p>

            <div class="btn-div">
                <button class="dark hover">Costum Order</button>
                <button class="gray hover">Existing Inventory</button>
            </div>
        </div>

    </div>
    {/each}
    {/if}
    {#if orientation == 'portrait'}
    {#each Mimages as image}
    <div style="background: url({image.img});height: 100vh;width: 100vw;background-size: 100vw 100vh;background-position: top;scroll-snap-align: start;" class="textAlign">
        <div class="infoDiv">
            <h1>{image.text1}</h1>
            <p>{image.text2}</p>

            <div class="btn-div">
                <button class="dark hover">Costum Order</button>
                <button class="gray hover">Existing Inventory</button>
            </div>
        </div>


    </div>
    {/each}
    {/if}

</div>

<style>

    .div {
        scroll-snap-type: y mandatory;
        height: 100vh;
        overflow-y: scroll;
        overflow-x: hidden;

    }


    .textAlign {
        display: flex;
        align-items: center;

    }

    .infoDiv {
    display: grid;
    grid-template-rows: 1fr 1fr;
     margin-left: auto;
     margin-right: auto;
     letter-spacing: normal;
    }

    @media (orientation: portrait) {
        .infoDiv{
            font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
            margin-top: 10vh;
        }

        button {
          width: 60vh;  
        }
    }

    .btn-div {
        margin-top: 40vh;
    }

    button {
        margin-top: 2vh;
        width: 40vh;
        font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
        font-weight: bolder;
    }

    .gray {
        color: whitesmoke;
    }

    .gray:hover {
        color: black;
    }

    .dark {
        background-color: azure;
        color: black;
    }

</style>
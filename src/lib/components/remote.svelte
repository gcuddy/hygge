<script>
	import { createEventDispatcher } from "svelte";



    const dispatch = createEventDispatcher();

</script>
<div class="remote" on:click>
    <div class="buttons">
        <!-- <button>Menu</button> -->
    </div>

    <div class="play-button-row">
        <button on:click|stopPropagation={(e) => {
            dispatch('playpause');
        }} class="play-button">
            <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" fill="#000000" viewBox="0 0 256 256"><path d="M184,64V192a8,8,0,0,1-16,0V64a8,8,0,0,1,16,0Zm40-8a8,8,0,0,0-8,8V192a8,8,0,0,0,16,0V64A8,8,0,0,0,224,56Zm-80,72a15.76,15.76,0,0,1-7.33,13.34L48.48,197.49A15.91,15.91,0,0,1,24,184.15V71.85A15.91,15.91,0,0,1,48.48,58.51l88.19,56.15A15.76,15.76,0,0,1,144,128Zm-16.18,0L40,72.08V183.93Z"></path></svg>
        </button>
    </div>

</div>


<style>
    .remote {
        background: black;
        border-radius: 4px;
        border: 1px solid white;
        height: 400px;
        width: 200px;
        display: grid;
        grid-template-rows: repeat(3, 1fr);
        z-index: 50;
    }
    .buttons {
        display: grid;
        place-items: center;
    }

    .buttons button {
        /* border: 3px solid white; */
        border: none;
        background: lightgray;
        padding: 4px 8px;
        border-radius: 4px;
    }

    .play-button-row {
        display: grid;
        place-items: center;
        padding: 4px;
        /* background: red; */
    }

    .play-button {
        /* width: 100%; */
        /* flex: 1; */
        border-radius: 99999px;
        aspect-ratio: 1/1;
        padding: 12px;
        background: lightgray;
        border: 3px solid white;
        width: 75%;
    }
</style>

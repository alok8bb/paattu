<script>
	let volume = 0.7;
	import { audioElement } from '$lib/store'
	
	$: percentage = (volume/1) * 100;

	function setVolume() {
        // volume = Math.max(0, Math.min(1, volume));
        $audioElement.volume = volume;
    }

    function mutetoggle() {
        $audioElement.muted = !$audioElement.muted
    }
</script>
<div class="volume flex flex-jc flex-ac">
    <svg on:click={mutetoggle} xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 32 32"><path fill="currentColor" d="M18 5.433c0-1.398-1.742-2.036-2.645-.97l-4.086 4.83A2 2 0 0 1 9.743 10H6a4 4 0 0 0-4 4v4a4 4 0 0 0 4 4h3.743a2 2 0 0 1 1.526.708l4.086 4.829c.902 1.066 2.645.428 2.645-.97V5.434Zm3.433 3.743a1 1 0 0 1 1.391.258c1.465 2.13 2.238 4.324 2.238 6.566s-.773 4.436-2.238 6.567a1 1 0 1 1-1.648-1.133c1.285-1.87 1.887-3.676 1.887-5.434s-.602-3.564-1.887-5.433a1 1 0 0 1 .258-1.39Zm4.257-3.9a1 1 0 0 0-1.38 1.448c2.387 2.273 3.628 5.739 3.628 9.276c0 3.538-1.241 7.003-3.628 9.276a1 1 0 0 0 1.38 1.448c2.863-2.727 4.247-6.761 4.247-10.724S28.553 8.003 25.69 5.276Z"/></svg>
    <input
        name="volume"
        type="range"
        min="0"
        max="1"
        step="0.1"
        bind:value={volume}
        on:input={setVolume}
        style="--value: {percentage.toString() + "%"}"
    />
</div>

 <style>
    div.volume {
        gap: 0.5rem;
        width: 30%;
    }
 </style>
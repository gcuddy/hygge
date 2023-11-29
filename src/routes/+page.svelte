<script lang="ts">
	import Fire from '$lib/components/fire.svelte';
	import Remote from '$lib/components/remote.svelte';
	import Tv from '$lib/components/tv.svelte';
	import { onMount } from 'svelte';
	import { fly } from 'svelte/transition';

	let iframe: HTMLIFrameElement;

	onMount(() => {
		if (iframe) {
			iframe.contentWindow?.postMessage('{"event":"listening","id":1,"channel":"widget"}', '*');
		}
	});
	let showRemote = true;
    let showIframe = false;
</script>

<svelte:head>
	<script src="https://www.youtube.com/iframe_api"></script>
</svelte:head>

<div class="artwork"></div>

<div class="artwork2"></div>
<Tv>
	{#if showIframe}
		<iframe
			bind:this={iframe}
			width="100%"
			height="100%"
			src="https://www.youtube.com/embed/CdMUOsf2QNc?autoplay=1&controls=0&rel=0&enablejsapi=1"
			title="YouTube video player"
			frameborder="0"
			allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
			allowfullscreen
		></iframe>
	{/if}
</Tv>
<Fire />

<div class="remote" style:transform="translateY({showRemote ? '30px' : '300px'})">
	<Remote
		on:click={() => {
			showRemote = !showRemote;
		}}
		on:playpause={() => {
            showIframe = true;
			iframe.contentWindow?.postMessage('{"event":"command","func":"playVideo","args":""}', '*');
			showRemote = false;
		}}
	/>
</div>

<style>
	.remote {
		position: absolute;
		bottom: 0;
		z-index: 2;
		transition-property: transform;
		transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
		transition-duration: 300ms;
	}
	.artwork {
		position: absolute;
		top: 40px;
		left: 40px;
		height: 200px;
		width: 200px;
		border: 1px solid white;
        background-image: url('/bg.svg');
	}

    .artwork2 {
		position: absolute;
		top: 40px;
		right: 30px;
		height: 400px;
		width: 400px;
		border: 1px solid white;
        background-image: url('/bg.svg');
        filter: hue-rotate(180deg);
	}
</style>

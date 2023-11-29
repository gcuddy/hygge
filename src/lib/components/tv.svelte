<div class="tv">
	<slot />
</div>

<style>
	.tv {
		border: 1px solid white;
		/* padding: 4rem; */
		width: min(100vw, 60rem);
		aspect-ratio: 16/9;
        background: black;
		z-index: 99;
	}
</style>

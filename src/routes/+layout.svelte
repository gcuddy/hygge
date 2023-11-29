<div>
	<slot />
</div>

<style>
    :global(body) {
        margin: 0;
    }
	div {
		background-color: black;
		color: white;
		display: grid;
		place-items: center;
		height: 100vh;
	}
</style>

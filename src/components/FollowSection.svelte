<script>
	import Inview from 'svelte-inview';

	let ref;
</script>

<section bind:this={ref} class="white-section">
	<div id="follow" class="container">
		<Inview let:inView wrapper={ref}>
			{#if inView}
				<h2 class="heading expandText">Follow me on <span>Spotify</span></h2>
			{:else}
				<h2 class="heading">Follow me on <span>Spotify</span></h2>
			{/if}
		</Inview>
		<div class="content">
			<iframe
				title="follow me"
				class="spotify-frame"
				src="https://open.spotify.com/follow/1/?uri=spotify:artist:3sS1ofnjxVvkF6p2TeDKnD?si=P5_SzBgVTzWj6J6ndYfhOw&amp;size=detail&amp;theme=light"
				scrolling="no"
				frameborder="0"
				allowtransparency="true" />
		</div>
	</div>
</section>

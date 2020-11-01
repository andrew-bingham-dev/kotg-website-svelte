<script>
	import { onMount } from 'svelte';
	import axios from 'axios';

	let error = null;
	let baseURL = 'http://localhost:1337';
	let bio = {};
	let imageURL = '';

	onMount(async () => {
		try {
			const res = await axios.get('http://localhost:1337/bio');
			bio = res.data;
		} catch (e) {
			error = e;
		}

		imageURL = baseURL + bio.image.formats.small.url;
	});
</script>

<section class="black-section">
	<div id="bio" class="container">
		<h2 class="heading">BIO</h2>
		<div class="content">
			{#if error !== null}
				{error}
			{:else}
				<p>{bio.article}</p>
				<img src={imageURL} alt="artist" />
			{/if}
		</div>
	</div>
</section>

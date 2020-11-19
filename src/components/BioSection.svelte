<script>
	import { onMount } from 'svelte';
	import Inview from 'svelte-inview';
	import axios from 'axios';
	import * as Global from '../global.js';

	let error = null;
	let bio = {};
	let imageURL = '';
	let ref;

	onMount(async () => {
		try {
			const res = await axios.get(Global.baseURL + '/bio');
			bio = res.data;
		} catch (e) {
			error = e;
		}

		imageURL = Global.baseURL + bio.image.formats.small.url;
	});
</script>

<section bind:this={ref} class="black-section">
	<div id="bio" class="container">
		<Inview let:inView wrapper={ref}>
			{#if inView}
				<h2 class="heading expandText">BIO</h2>
			{:else}
				<h2 class="heading">BIO</h2>
			{/if}
		</Inview>
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

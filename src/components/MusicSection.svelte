<script>
	import { onMount } from 'svelte';
	import axios from 'axios';
	import FeaturedSong from './FeaturedSong.svelte';
	import * as Global from '../global.js';
	import Inview from 'svelte-inview';

	let error = null;
	let songs = [];
	let ref;

	onMount(async () => {
		try {
			const res = await axios.get(Global.baseURL + '/songs');
			songs = res.data;
		} catch (e) {
			error = e;
		}
	});
</script>

<section bind:this={ref} class="black-section">
	<div id="music" class="container">
		<Inview let:inView wrapper={ref}>
			{#if inView}
				<h2 class="heading expandText">Featured music</h2>
			{:else}
				<h2 class="heading">Featured music</h2>
			{/if}
		</Inview>
	</div>
</section>
{#if error !== null}
	{error}
{:else}
	{#each songs as song}
		{#if song.featured != false}
			<FeaturedSong
				colourTheme={song.id % 2 == 0 ? 'white' : 'black'}
				songImage={Global.baseURL + song.song_image.formats.medium.url}
				songTitle={song.title}
				songReleaseDate={song.release_date}
				playSpotifyLink={song.play_link1}
				playAppleLink={song.play_link2}
				playYoutubeLink={song.play_link3}
				buyAmazonLink={song.buy_link1}
				buyGoogleLink={song.buy_link2}
				buyNapsterLink={song.buy_link3} />
		{/if}
	{/each}
{/if}

<script>
	import { onMount } from 'svelte';
	import axios from 'axios';
	import FeaturedSong from './FeaturedSong.svelte';

	let error = null;
	let songs = [];
	let baseURL = 'http://localhost:1337';

	onMount(async () => {
		try {
			const res = await axios.get('http://localhost:1337/songs');
			songs = res.data;
		} catch (e) {
			error = e;
		}
	});
</script>

<section class="black-section">
	<div id="music" class="container">
		<h2 class="heading">Featured music</h2>
	</div>
</section>
{#if error !== null}
	{error}
{:else}
	{#each songs as song}
		<FeaturedSong
			colourTheme={song.id % 2 == 0 ? 'white' : 'black'}
			songImage={baseURL + song.song_image.formats.medium.url}
			songTitle={song.title}
			songReleaseDate={song.release_date}
			playSpotifyLink={song.play_link1}
			playAppleLink={song.play_link2}
			playYoutubeLink={song.play_link3}
			buyAmazonLink={song.buy_link1}
			buyGoogleLink={song.buy_link2}
			buyNapsterLink={song.buy_link3} />
	{/each}
{/if}

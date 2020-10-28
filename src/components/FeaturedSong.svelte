<script lang="ts">
	export let colourTheme: string;
	export let songImage: string;
	export let songTitle: string;
	export let songReleaseDate: string;
	export let playSpotifyLink: string;
	export let playAppleLink: string;
	export let playYoutubeLink: string;
	export let buyAmazonLink: string;
	export let buyGoogleLink: string;
	export let buyNapsterLink: string;
</script>

<section class="{colourTheme}-section">
	<div class="container">
		<div class="song {colourTheme}-song">
			<img class="song-img" src={songImage} alt="song art" />
			<div class="song-details">
				<h3>Title</h3>
				<h4>{songTitle}</h4>
				<br />
				<h3>Release date</h3>
				<h4>{songReleaseDate}</h4>
				<br />
			</div>
			<div class="song-play-options">
				<h3 class="btn-heading">Play this song on</h3>
				<button class="play-spotify">
					<a href={playSpotifyLink}><h3>Spotify</h3></a>
				</button>
				<button class="play-apple">
					<a href={playAppleLink}><h3>Apple Music</h3></a>
				</button>
				<button class="play-youtube">
					<a href={playYoutubeLink}><h3>YouTube</h3></a>
				</button>
			</div>
			<div class="song-buy-options">
				<h3 class="btn-heading">Buy this song on</h3>
				<button class="buy-amazon">
					<a href={buyAmazonLink}><h3>Amazon</h3></a>
				</button>
				<button class="buy-google">
					<a href={buyGoogleLink}><h3>Google Music</h3></a>
				</button>
				<button class="buy-napster">
					<a href={buyNapsterLink}><h3>Napster</h3></a>
				</button>
			</div>
		</div>
	</div>
</section>

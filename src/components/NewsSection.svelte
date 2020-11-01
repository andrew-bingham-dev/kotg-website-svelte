<script>
	import { onMount } from 'svelte';
	import NewsPost from './NewsPost.svelte';
	import axios from 'axios';

	let blogs = [];
	let error = null;

	onMount(async () => {
		try {
			const res = await axios.get('http://localhost:1337/blogs');
			blogs = res.data;
		} catch (e) {
			error = e;
		}
	});
</script>

<section class="white-section">
	<div id="news" class="container">
		<h2 class="heading">Latest news</h2>
		<div class="content">
			{#if error !== null}
				{error}
			{:else}
				{#each blogs as blog}
					<NewsPost PostDate={blog.date} PostTitle={blog.title} PostArticle={blog.article} />
				{/each}
			{/if}
		</div>
	</div>
</section>

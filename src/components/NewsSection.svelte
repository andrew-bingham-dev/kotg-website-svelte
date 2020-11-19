<script>
	import { onMount } from 'svelte';
	import NewsPost from './NewsPost.svelte';
	import axios from 'axios';
	import * as Global from '../global.js';
	import Inview from 'svelte-inview';

	let blogs = [];
	let error = null;
	let ref;

	onMount(async () => {
		try {
			const res = await axios.get(Global.baseURL + '/blogs');
			blogs = res.data;
		} catch (e) {
			error = e;
		}
	});
</script>

<section bind:this={ref} class="white-section">
	<div id="news" class="container">
		<Inview let:inView wrapper={ref}>
			{#if inView}
				<h2 class="heading expandText">Latest news</h2>
			{:else}
				<h2 class="heading">Latest news</h2>
			{/if}
		</Inview>
		<div class="content">
			{#if error !== null}
				{error}
			{:else}
				{#each blogs as blog}
					{#if blog.featured == true}
						<NewsPost PostDate={blog.date} PostTitle={blog.title} PostArticle={blog.article} />
					{/if}
				{/each}
			{/if}
		</div>
	</div>
</section>

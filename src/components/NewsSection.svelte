<script>
	import NewsPost from './NewsPost.svelte';
</script>

<section class="white-section">
	<div id="news" class="container">
		<h2 class="heading">Latest news</h2>
		<div class="content">
			<NewsPost
				PostDate="1st September 2022"
				PostTitle="New song coming"
				PostArticle="Lorem ipsum dolor sit amet, consectetur adipisicing elit." />
			<NewsPost
				PostDate="1st September 2021"
				PostTitle="New song coming"
				PostArticle="Lorem ipsum dolor sit amet, consectetur adipisicing elit." />
			<NewsPost
				PostDate="1st September 2020"
				PostTitle="New song coming"
				PostArticle="Lorem ipsum dolor sit amet, consectetur adipisicing elit." />
		</div>
	</div>
</section>

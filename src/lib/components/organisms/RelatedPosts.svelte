<script lang="ts">
	import BlogPostCard from '$lib/components/molecules/BlogPostCard.svelte';
	import type { BlogPost } from '$lib/utils/types';

	export let posts: BlogPost[];
</script>

<div class="container">
	<div class="grid">
		{#each posts as post}
			<BlogPostCard
				slug={post.slug}
				title={post.title}
				date={post.date}
				contributor={post.contributor}
				coverImage={post.coverImage}
			/>
		{/each}
	</div>
</div>

<style lang="scss">
	@import '$lib/scss/breakpoints.scss';

	.container {
		color: rgba(245, 245, 245, 0.8);
		background: rgba(26, 26, 26, 1);
		padding-bottom: 64px;
	}

	.grid {
		width: 100%;
		display: grid;
		grid-template-columns: 1fr;
		grid-gap: 20px;

		@include for-tablet-portrait-up {
			grid-template-columns: 1fr 1fr;
		}

		@include for-desktop-up {
			grid-template-columns: 1fr 1fr 1fr;
		}
	}
</style>

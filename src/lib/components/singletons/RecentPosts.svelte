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
				coverImage={post.coverImage}
				contributor={post.contributor}
			/>
		{/each}
	</div>
</div>

<style lang="scss">
	@import '$lib/scss/breakpoints.scss';

	.container {
		display: flex;
		flex-direction: column;
		margin: 0 auto;
		padding-top: 3rem;
		background: rgba(26, 26, 26, 1);
		color: rgba(245, 245, 245, 0.96);
		padding-bottom: 64px;
		box-sizing: border-box;

		@include for-desktop-up {
			max-width: 1200px;
		}
	}

	.grid {
		padding-top: 3rem;
		width: 100%;
		display: grid;
		grid-template-columns: 1fr 1fr;
		grid-gap: 20px;

		@include for-phone-only {
			grid-template-columns: 1fr;
		}

		@include for-tablet-landscape-up {
			grid-template-columns: 1fr 1fr;
		}

		@include for-desktop-up {
			grid-template-columns: 1fr 1fr 1fr;
		}
	}
</style>

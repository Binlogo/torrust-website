<script lang="ts">
	import { formatDate } from '$lib/utils/date';

	export let title: string;
	export let coverImage: string | undefined = undefined;
	export let slug: string;
	export let date: string;
	export let contributor: string;

	const formattedDate = formatDate(date);
</script>

<a href="/blog/{slug}" class="container">
	<div class="grid">
		<div class="image-container">
			<img src={coverImage} alt={title} />
		</div>
		<div class="text-container">
			<h2>{title}</h2>
			{#if contributor}
				<p>{contributor} - {formattedDate}</p>
			{:else}
				<p>{formattedDate}</p>
			{/if}
		</div>
	</div>
</a>

<style lang="scss">
	@import '$lib/scss/breakpoints.scss';

	a {
		position: relative;
		display: block;
		width: 100%;
		overflow: hidden;
		color: rgba(245, 245, 245, 0.96);
		text-decoration: none;
		cursor: pointer;
	}

	a:hover {
		color: rgba(255, 49, 0, 1);
	}

	.grid {
		position: relative;
		width: 100%;
		height: 300px;
	}

	.image-container {
		width: 100%;
		height: 100%;
		overflow: hidden;
		border-radius: 10px;
	}

	.image-container img {
		width: 100%;
		height: 100%;
		object-fit: cover;
	}

	.text-container {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		display: flex;
		flex-direction: column;
		justify-content: flex-end;
		align-items: flex-start;
		text-align: left;
		color: white;
		background: rgba(0, 0, 0, 0.5); /* Dark overlay for better readability */
		padding: 1rem;
		transition: background 0.3s ease;
	}

	.text-container:hover {
		color: rgba(255, 49, 0, 1);
	}

	.text-container h2 {
		margin: 0;
		font-size: 1.5rem;
		word-break: keep-all;
	}

	.text-container p {
		margin: 0.5rem 0 0;
		font-size: 0.875rem;
		color: #f5f5f5;
	}

	a:hover .text-container {
		background: rgba(0, 0, 0, 0.7); /* Darken overlay on hover */
	}
</style>

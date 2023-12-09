<script lang="ts">
	import { titles } from '$lib/deck/titles';
	import { page } from '$app/stores';
	import Reveal from '$lib/deck/reveal.svelte';
	$: decodedLocation = '';
	$: neigbors = findNeigbors($page.url.pathname);
	function findNeigbors(pathname: string) {
		let location = pathname.split('/').at(-1)!;
		decodedLocation = decodeURIComponent(location);
		const currentIndex = titles.indexOf(decodedLocation);
		return [titles[currentIndex - 1], titles[currentIndex + 1]];
	}
</script>

<div class="section">
	<div class="navbar">
		<a href="/">DDoS</a>
		<h4>{decodedLocation}</h4>
		<div>
			{#if neigbors[0]}
				<a href="/titles/{neigbors[0]}">Previous</a>
			{/if}
			{#if neigbors[1]}
				<a href="/titles/{neigbors[1]}">Next</a>
			{/if}
		</div>
	</div>
	<div class="content">
		{#key $page.url.pathname}
			<Reveal mdFile={decodedLocation} />
	    {/key}
	</div>
</div>

<style>
	.section {
		display: flex;
		flex-direction: column;
	}
	.navbar{
		display: flex;
		z-index: 99;
		position: fixed;
		background-color: transparent;
	}
	.section div:first-child h4 {
		color: var(--primary800);
	}
	.section div:first-child {
		width: 100%;
		padding: 10px;
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding-inline: 5%;
	}

	.section > div > a {
		font-size: var(--h3);
	}
	.section > div > div > a {
		font-size: 1rem;
		margin-left: 10px;
		gap: 10px;
	}
	.section > div > div{
		border: 1px solid rgb(39, 39, 39);
		background-color: rgb(20, 20, 20);
		padding: 5px;
		padding-right: 15px;
		border-radius: 20px;
	}
	.section > div > div > a:hover {
		color: var(--primary800);
	}

	@media screen and (width <768px) {
		.section div:first-child h4 {
			display: none;
		}
	}
</style>

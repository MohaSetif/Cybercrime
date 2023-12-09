<script lang="ts">
	import { titles } from '$lib/deck/titles';
	import { onMount } from 'svelte';
	import '../app.css';

	onMount(() => {
		const letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";

		let interval: any = null;

		const screen: HTMLElement | null = document.querySelector(".screen");
		const name: HTMLElement | null = document.querySelector(".name");

		if (!screen || !name) {
			return;
		}

		screen.onmouseenter = (event) => {
			let iteration = 0;

			clearInterval(interval);

			interval = setInterval(() => {
			if (name) {
				name.innerText = name.innerText
				.split("")
				.map((letter, index) => {
					if (index < iteration) {
					return name.dataset.value ? name.dataset.value[index] : letter;
					}

					return letters[Math.floor(Math.random() * 26)];
				})
				.join("");
			}

			if (iteration >= (name && name.dataset.value ? name.dataset.value.length : 0)) {
				clearInterval(interval);
			}

			iteration += 1 / 3;
			}, 30);
		};
    });
</script>

<div class="main">
    <div class="screen">  
		<div class="screen-overlay"></div>  
		<div class="screen-content">
			<div class="screen-user">
			<span class="name" data-value="Distributed Denial of Service">Distributed Denial of Service</span>
			<a class="link" href="/">Bourouba Med El Khalil</a>
			<a class="link" href="/">Keskas Aymen Islam</a>
			</div>
		</div>
	</div>
	<div class="links">
		{#each titles as title}
			<a href="/titles/{title}">{title}</a>
		{/each}
	</div>
</div>

<style>
	.main {
		width: 100vw;
		min-height: 100vh;
		height: fit-content;
		overflow-y: auto;
		display: block;
		justify-content: space-evenly;
		align-items: center;
		padding: 10px;
	}
	.links {
    	display: flex;
        gap: 20px;
        flex-wrap: wrap;
		margin-top: 10px;
		justify-content: center;
		align-items: center;
		padding: 30px;
    }
	.links a {
		background-color: var(--primary100);
		color: var(--primary800);
		font-size: var(--h4);
		padding-inline: 6px;
		padding-block: 4px;
		border-radius: 8px;
		border: 2px solid rgb(102, 62, 2);
		flex-grow: 1;
	}
	.links a:hover {
		background-color: var(--primary400);
		border: 2px solid rgb(255, 230, 90);
	}
	@media screen and (width <768px) {
		.main {
			flex-direction: column;
			align-items: center;
		}
		
		.links {
			display: flex;
			gap: 10px;
			width: 100%;
			align-items: center;
		}

		.links a{
		    font-size: 15px;
	    }
	}
</style>

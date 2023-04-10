<script lang="ts">
	import { onMount } from 'svelte';
	import Modal from './Modal.svelte';
	import { faShoppingCart } from '@fortawesome/free-solid-svg-icons';
	import Fa from 'svelte-fa/src/fa.svelte';

	interface Img {
		src: string;
		thumb: string;
		alt: string;
		link?: string;
	}

	function img(name: string, link?: string): Img {
		return {
			src: `Website/lubov_soltan-${name}.jpg`,
			thumb: `Website/lubov_soltan-${name}-sq1.jpg`,
			alt: `Artwork ${name}`,
			link
		};
	}

	const images: Img[] = [
		img('cluttered-backyard'),
		img('envy'),
		img('eyes-of-the-trees'),
		img('flock-leader'),
		img('ancestral-forest', 'https://www.thegallerygeorge.com/product-page/ancestral-forest'),
		img('bratislava', 'https://www.thegallerygeorge.com/product-page/bratislava'),
		img('cat', 'https://www.thegallerygeorge.com/product-page/cat'),
		img('full-moon'),
		img('house-on-the-water', 'https://www.thegallerygeorge.com/product-page/house-on-the-water'),
		img('night-forest', 'https://www.thegallerygeorge.com/product-page/night-forest'),
		img('perfect-day', 'https://www.thegallerygeorge.com/product-page/perfect-day'),
		img('rainy-street', 'https://www.thegallerygeorge.com/product-page/rainy-street'),
		img('toronto-after-rain', 'https://www.thegallerygeorge.com/product-page/toronto-after-rain'),
		img('toronto-shore', 'https://www.thegallerygeorge.com/product-page/toronto-shore'),
		img('abstract-green'),
		img('alien-landscape'),
		img('art-deco-man'),
		img('head-above-water'),
		img('head-in-the-wall'),
		img('lady-in-the-woods'),
		img('lillies'),
		img('liya'),
		img('rebirth'),
		img('snake'),
		img('the-gateway'),
		img('the-mask'),
		img('two-suns')
	];

	let currentImage: string | null = null;
	let currentAlt: string | null = null;
	let currentStoreLink: string | null = null;
	let showModal = false;

	$: if (!showModal) {
		currentImage = null;
		currentStoreLink = null;
	}
</script>

<div class="gallery">
	{#each images as img}
		<a
			href={'#'}
			on:click|preventDefault={() => {
				showModal = true;
				currentImage = img.src;
				currentAlt = img.alt;
				currentStoreLink = img.link ?? null;
			}}
		>
			<img class="image" alt={img.alt} src={img.thumb} />
		</a>
	{/each}
</div>

<Modal bind:showModal>
	<img class="modal-image" alt={`Viewing ${currentAlt}`} src={currentImage} />
	{#if currentStoreLink}
		<p class="call-to-action">
			<a target="_blank" href={currentStoreLink} alt={`Buy ${currentAlt} now`}
				><Fa icon={faShoppingCart} /> Buy now</a
			>
		</p>
	{/if}
</Modal>

<style>
	.gallery {
		display: flex;
		flex-wrap: wrap;
		align-items: flex-start;
		flex-direction: row;
		justify-content: space-between;
	}
	.gallery img {
		margin: 10px;
		width: 100%;
	}

	@media (min-width: 1024px) {
		.gallery a {
			width: 25%;
		}
	}

	@media (min-width: 480px) {
		.gallery a {
			width: 30%;
		}
	}

	@media (max-width: 480px) {
		.gallery a {
			width: 90%;
		}
	}

	.modal-image {
		max-height: 82vh;
	}
	.call-to-action {
		display: flex;
		align-items: center;
		justify-content: center;
	}
</style>

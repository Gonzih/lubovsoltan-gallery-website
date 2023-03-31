<script lang="ts">
 import { onMount } from 'svelte';
 import Modal from './Modal.svelte';
 import { faShoppingCart } from '@fortawesome/free-solid-svg-icons';
 import Fa from 'svelte-fa/src/fa.svelte';

 import cb from '$lib/images/Website/lubov_soltan-cluttered-backyard.jpg';
 import cbs from '$lib/images/Website/lubov_soltan-cluttered-backyard-sq1.jpg';
 import envy from '$lib/images/Website/lubov_soltan-envy.jpg';
 import envys from '$lib/images/Website/lubov_soltan-envy-sq1.jpg';
 import trees from '$lib/images/Website/lubov_soltan-eyes-of-the-trees.jpg';
 import treess from '$lib/images/Website/lubov_soltan-eyes-of-the-trees-sq1.jpg';
 import flock from '$lib/images/Website/lubov_soltan-flock-leader.jpg';
 import flocks from '$lib/images/Website/lubov_soltan-flock-leader-sq1.jpg';
 import ancestral from '$lib/images/Website/lubov_soltan-ancestral-forest.jpg';
 import ancestrals from '$lib/images/Website/lubov_soltan-ancestral-forest-sq1.jpg';
 import bratislava from '$lib/images/Website/lubov_soltan-bratislava.jpg';
 import bratislavas from '$lib/images/Website/lubov_soltan-bratislava-sq1.jpg';
 import cat from '$lib/images/Website/lubov_soltan-cat.jpg';
 import cats from '$lib/images/Website/lubov_soltan-cat-sq1.jpg';
 import fullmoon from '$lib/images/Website/lubov_soltan-full-moon.jpg';
 import fullmoons from '$lib/images/Website/lubov_soltan-full-moon-sq1.jpg';
 import houses from '$lib/images/Website/lubov_soltan-house-on-the-water-sq1.jpg'
 import house from '$lib/images/Website/lubov_soltan-house-on-the-water.jpg'
 import forests from '$lib/images/Website/lubov_soltan-night-forest-sq1.jpg'
 import forest from '$lib/images/Website/lubov_soltan-night-forest.jpg'
 import perfectday from '$lib/images/Website/lubov_soltan-perfect-day.jpg'
 import perfectdays from '$lib/images/Website/lubov_soltan-perfect-day-sq1.jpg'
 import rainystreets from '$lib/images/Website/lubov_soltan-rainy-street-sq1.jpg'
 import rainystreet from '$lib/images/Website/lubov_soltan-rainy-street.jpg'
 import torontorains from '$lib/images/Website/lubov_soltan-toronto-after-rain-sq1.jpg'
 import torontorain from '$lib/images/Website/lubov_soltan-toronto-after-rain.jpg'
 import torontoshores from '$lib/images/Website/lubov_soltan-toronto-shore-sq1.jpg'
 import torontoshore from '$lib/images/Website/lubov_soltan-toronto-shore.jpg'

 // import from '$lib/images/Website/lubov_soltan-abstract-green-sq1.jpg'
 // import from '$lib/images/Website/lubov_soltan-abstract-green.jpg'
 // import from '$lib/images/Website/lubov_soltan-alien-landscape.jpg'
 // import from '$lib/images/Website/lubov_soltan-art-deco-man-sq1.jpg'
 // import from '$lib/images/Website/lubov_soltan-art-deco-man.jpg'
 // import from '$lib/images/Website/lubov_soltan-head-above-water-sq1.jpg'
 // import from '$lib/images/Website/lubov_soltan-head-above-water.jpg'
 // import from '$lib/images/Website/lubov_soltan-head-in-the-wall-sq1.jpg'
 // import from '$lib/images/Website/lubov_soltan-head-in-the-wall.jpg'
 // import from '$lib/images/Website/lubov_soltan-lady-in-the-woods.jpg'
 // import from '$lib/images/Website/lubov_soltan-lady-of-the-woods-sq1.jpg'
 // import from '$lib/images/Website/lubov_soltan-lillies-sq1.jpg'
 // import from '$lib/images/Website/lubov_soltan-lillies.jpg'
 // import from '$lib/images/Website/lubov_soltan-liya-sq1.jpg'
 // import from '$lib/images/Website/lubov_soltan-liya.jpg'
 // import from '$lib/images/Website/lubov_soltan-rebirth-sq1.jpg'
 // import from '$lib/images/Website/lubov_soltan-rebirth.jpg'
 // import from '$lib/images/Website/lubov_soltan-snake-sq1.jpg'
 // import from '$lib/images/Website/lubov_soltan-snake.jpg'
 // import from '$lib/images/Website/lubov_soltan-the-gateway-sq1.jpg'
 // import from '$lib/images/Website/lubov_soltan-the-gateway.jpg'
 // import from '$lib/images/Website/lubov_soltan-the-mask-sq1.jpg'
 // import from '$lib/images/Website/lubov_soltan-the-mask.jpg'
 // import from '$lib/images/Website/lubov_soltan-two-suns-sq1.jpg'
 // import from '$lib/images/Website/lubov_soltan-two-suns.jpg'

 interface Img {
   src: string;
   thumb: string;
   link?: string;
 }

 const images: Img[] = [
   {src: cb, thumb: cbs},
   {src: envy, thumb: envys},
   {src: trees, thumb: treess},
   {src: flock, thumb: flocks},
   {src: ancestral, thumb: ancestrals, link: "https://www.thegallerygeorge.com/product-page/ancestral-forest"},
   {src: bratislava, thumb: bratislavas, link: "https://www.thegallerygeorge.com/product-page/bratislava"},
   {src: cat, thumb: cats, link: "https://www.thegallerygeorge.com/product-page/cat"},
   {src: fullmoon, thumb: fullmoons},
   {src: house, thumb: houses, link: "https://www.thegallerygeorge.com/product-page/house-on-the-water"},
   {src: forest, thumb: forests, link: "https://www.thegallerygeorge.com/product-page/night-forest"},
   {src: perfectday, thumb: perfectdays, link: "https://www.thegallerygeorge.com/product-page/perfect-day"},
   {src: rainystreet, thumb: rainystreets, link: "https://www.thegallerygeorge.com/product-page/rainy-street"},
   {src: torontorain, thumb: torontorains, link: "https://www.thegallerygeorge.com/product-page/toronto-after-rain"},
   {src: torontoshore, thumb: torontoshores, link: "https://www.thegallerygeorge.com/product-page/toronto-shore"},
 ];

 let currentImage: string | null = null;
 let currentStoreLink: string | null = null;
 let showModal = false;

 $: if (!showModal) {
   currentImage = null;
   currentStoreLink = null;
 }
</script>

<div class="gallery">
  {#each images as img}
    <a href={"#"} on:click|preventDefault={() => {
                          showModal = true;
                          currentImage = img.src;
                          currentStoreLink = img.link ?? null;
                          }} >
      <img class="image" alt="Gallery" src={img.thumb} />
    </a>
  {/each}
</div>

<Modal bind:showModal>
  <img class="modal-image" alt="Modal" src={currentImage} />
  {#if currentStoreLink}
    <p class="call-to-action">
      <a target="_blank" href={currentStoreLink} alt="Buy now"><Fa icon={faShoppingCart} />  Buy now</a>
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
    max-width: 20vw;
  }

	@media (max-width: 720px) {
    .gallery img {
      max-width: 40vw;
    }
	}

	@media (min-width: 720px) and (max-width: 1024px) {
    .gallery img {
      max-width: 28vw;
    }
	}

	@media (max-width: 480px) {
    .gallery img {
      max-width: 90vw;
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

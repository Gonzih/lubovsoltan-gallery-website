<script lang="ts">
 import Modal from './Modal.svelte';
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

 interface Img {
   src: string;
   thumb: string;
 }

 const images: Img[] = [
   {src: cb, thumb: cbs},
   {src: envy, thumb: envys},
   {src: trees, thumb: treess},
   {src: flock, thumb: flocks},
   {src: ancestral, thumb: ancestrals},
   {src: bratislava, thumb: bratislavas},
   {src: cat, thumb: cats},
 ];

 let currentImage: string | null = null;
 let showModal = false;

 $: if (!showModal) {
   currentImage = null;
 }
</script>

<div class="gallery">
  {#each images as img}
    <a href={""} on:click={() => {
                          showModal = true;
                          currentImage = img.src;
                          }} >
      <img class="image" alt="Gallery" src={img.thumb} />
    </a>
  {/each}
</div>

<Modal bind:showModal>
  <img class="modal-image" alt="Modal" src={currentImage} />
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
 .modal-image {
   max-height: 90vh;
 }
</style>

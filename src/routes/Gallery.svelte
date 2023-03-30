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

 interface Img {
   src: string;
   thumb: string;
 }

 const images: Img[] = [
   {src: cb, thumb: cbs},
   {src: envy, thumb: envys},
   {src: trees, thumb: treess},
   {src: flock, thumb: flocks},
 ];

 let currentImage: string | null = null;
 let showModal = false;
</script>

<div class="gallery">
  {#each images as img}
    <a href={"#img"} on:click={() => {
                          currentImage = img.src;
                          showModal = true;
                          }} >
      <img class="image" alt="Gallery" src={img.thumb} />
    </a>
  {/each}
</div>

<Modal bind:showModal on:close={() => alert(1)}>
  <img class="modal-image" alt="Modal" src={currentImage} />
</Modal>

<style>
  .gallery {
    display: flex;
    flex-wrap: wrap;
    align-items: flex-start;
    flex-direction: row;
  }
  .gallery img {
    margin: 10px;
    max-width: 20vw;
  }
 .modal-image {
   max-height: 90vh;
 }
</style>

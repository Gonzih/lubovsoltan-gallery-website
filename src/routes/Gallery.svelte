<script lang="ts">
 import Modal from './Modal.svelte';

 const images: string[] = [
   "https://picsum.photos/id/1/3000/4000",
   "https://picsum.photos/id/1/3000/4000",
   "https://picsum.photos/id/1/3000/4000",
   "https://picsum.photos/id/1/3000/4000",
   "https://picsum.photos/id/1/3000/4000",
   "https://picsum.photos/id/1/3000/4000",
   "https://picsum.photos/id/1/3000/4000",
   "https://picsum.photos/id/1/3000/4000",
   "https://picsum.photos/id/1/3000/4000",
   "https://picsum.photos/id/1/3000/4000",
   "https://picsum.photos/id/1/3000/4000",
   "https://picsum.photos/id/1/3000/4000",
 ];

 let currentImage: string | null = null;
 let showModal = false;
</script>

<div class="gallery">
  {#each images as img}
    <a href={null} on:click={() => {
                          showModal = true;
                          currentImage = img;
                          }} >
      <img class="image" alt="Gallery" src={img} />
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
  }
  .gallery img {
    margin: 10px;
    border: 3px solid #000;
    box-shadow: 3px 3px 8px 0px rgba(0,0,0,0.3);
    max-width: 23vw;
  }
 .modal-image {
   max-width: 100%;
 }
</style>

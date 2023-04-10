<script>
	import Header from './Header.svelte';
	import './styles.css';
	import Fa from 'svelte-fa/src/fa.svelte';
	import { faEnvelope, faStore } from '@fortawesome/free-solid-svg-icons';
	import { faInstagram, faTwitter, faBehance } from '@fortawesome/free-brands-svg-icons';
</script>

<div class="app">
	<Header />

	<main>
		<slot />
	</main>

	<footer>
		<p class="links">
			<a href="mailto:lubovsoltan@gmail.com"><Fa icon={faEnvelope} /></a>
			<a target="_blank" href="https://www.instagram.com/artist.lubov/"><Fa icon={faInstagram} /></a
			>
			<a target="_blank" href="https://twitter.com/Lubov_Soltan"><Fa icon={faTwitter} /></a>
			<a target="_blank" href="https://www.behance.net/lubovsoltan"><Fa icon={faBehance} /></a>
			<a target="_blank" href="https://www.thegallerygeorge.com/lubov-soltan"
				><Fa icon={faStore} /></a
			>
		</p>
	</footer>
</div>

<style>
	.links a {
		padding: 8px;
		font-size: 25px;
	}

	.app {
		display: flex;
		flex-direction: column;
		min-height: 100vh;
	}

	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		max-width: 64rem;
		margin: 0 auto;
		box-sizing: border-box;
	}

	footer {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding: 12px;
	}

	footer a {
		font-weight: bold;
	}

	@media (min-width: 480px) {
		footer {
			padding: 12px 0;
		}
	}
</style>

<script>
	import { Section } from '@sveltejs/site-kit/components';
	import Hero from './_home/Hero.svelte';
	import Supporters from './_home/Supporters/index.svelte';
	import Testimonials from './_home/Testimonials.svelte';
	import Companies from './_home/Companies.svelte';
	import Video from './_home/Video.svelte';
	import Community from './_home/Community.svelte';
	import Footer from './_home/Footer.svelte';
</script>

<svelte:head>
	<title>Svelte • 우리 모두를 위한 웹 개발</title>

	<meta name="twitter:title" content="Svelte" />
	<meta name="twitter:description" content="우리 모두를 위한 웹 개발" />
	<meta name="Description" content="우리 모두를 위한 웹 개발" />
</svelte:head>

<div class="home">
	<h1 class="visually-hidden">Svelte</h1>

	<Hero />

	<Testimonials />

	<Companies />

	<Section>
		<figure>
			<Video />
			<figcaption>
				<a href="https://www.offerzen.com/community/svelte-origins-documentary"
					>Watch the full Svelte Origins documentary</a
				>
			</figcaption>
		</figure>
	</Section>

	<Community />

	<Supporters />

	<Footer />
</div>

<style>
	figcaption {
		font: var(--sk-font-ui-medium);
	}

	.home :global {
		@media (min-width: 800px) {
			h2 {
				font: var(--sk-font-h1);
			}
		}
	}
</style>

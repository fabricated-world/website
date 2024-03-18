<script lang="ts">
	import SocialCard from '$lib/components/SocialCard.svelte';
</script>

<svelte:head>
	<title>Welcome to fabricated!</title>

	<meta name="darkreader-lock" />
</svelte:head>

<hgroup>
	<h1>fabricated.world</h1>
	<h2>Check our <a href="blog">Blog</a></h2>
	<div>
		<SocialCard
			text="Join our server!"
			url="https://discord.gg/t7U4xD7QyZ"
			logo="https://assets-global.website-files.com/6257adef93867e50d84d30e2/653714c1f22aef3b6921d63d_636e0a6ca814282eca7172c6_icon_clyde_white_RGB.svg"
			alt="discord"
			back_color="#5865F2"
   text_color="#fff"
		/>
	</div>
</hgroup>

<style>
	hgroup {
		width: 100%;
		height: 100%;

		gap: var(--size-2);

		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;

		padding: var(--size-7) var(--size-8);
	}

	h1,
	h2 {
		font-family: var(--font-mono);
	}

	h1 {
		text-shadow: #0aa 0 0 50px;
		font-size: var(--font-size-5);
	}

	h2 {
		font-size: var(--font-size-4);
	}

	div {
		width: fit-content;
		margin-top: var(--size-8);
	}

	@media (min-width: 564px) {
		h1 {
			font-size: var(--font-size-6);
		}

		h2 {
			font-size: var(--font-size-5);
		}
	}

	@media (min-width: 768px) {
		h1 {
			font-size: var(--font-size-8);
		}

		h2 {
			font-size: var(--font-size-7);
		}

		div {
			margin-top: var(--size-3);
		}
	}

	a {
		display: inline-block;
	}
</style>

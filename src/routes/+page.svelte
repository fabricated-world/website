<svelte:head>
	<title>Welcome to fabricated!</title>

	<meta name="darkreader-lock" />
</svelte:head>

<!--Actual content-->
<div class="page-content text-box">
	<p class="text title blur">fabricated.world</p>
	<p class="text subtitle">- coming soon -</p>
	<p class="text small">Check our ​<a href="blog">Blog</a></p>
</div>

<style>
	.page-content {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
	}
	.text-box {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.text {
		color: var(--text-1);
		font-family: 'JetBrains Mono', monospace;
		display: inline-flex;
	}
	.title {
		font-size: 100px;
	}
	.subtitle {
		margin-top: 15px;
		font-size: 50px;
	}
	.small {
		margin-top: 5px;
		font-size: 25px;
	}
	.blur {
		text-shadow: #0aa 0 0 50px;
	}
</style>

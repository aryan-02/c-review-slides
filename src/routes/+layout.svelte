<script lang="ts">
	import '../styles/app.css'
	export const prerender = true;
	let { children } = $props()
</script>

<svelte:head>
	<title>CSE 3318 - C Review</title>
	<link rel="preconnect" href="https://fonts.googleapis.com" />
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
	<link
		href="https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap"
		rel="stylesheet"
	/>
</svelte:head>

{@render children()}

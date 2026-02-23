<script lang="ts">
	import '../app.css';
	import Header from '$lib/components/Header.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import { initThemeListener } from '$lib/stores/theme';
	import { onMount } from 'svelte';

	let { children } = $props();

	onMount(() => {
		initThemeListener();
	});
</script>

<svelte:head>
	<title>First Baptist Church Wimberley</title>
	<meta name="description" content="To truly know Jesus and to make His truth known. Join us Sundays at 9:30AM and 11:00AM in Wimberley, Texas." />
</svelte:head>

<Header />
<main>
	{@render children()}
</main>
<Footer />

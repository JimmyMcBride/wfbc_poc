<script lang="ts">
	const images = [
		'https://fbcwimberley.com/wp-content/uploads/2025/07/102A6470-scaled.jpg',
		'https://fbcwimberley.com/wp-content/uploads/2025/07/102A6447-scaled.jpg',
		'https://fbcwimberley.com/wp-content/uploads/2025/07/102A5443-scaled.jpg'
	];

	let currentSlide = $state(0);

	$effect(() => {
		const interval = setInterval(() => {
			currentSlide = (currentSlide + 1) % images.length;
		}, 5000);
		return () => clearInterval(interval);
	});
</script>

<section class="relative min-h-screen flex items-end justify-center overflow-hidden">
	{#each images as src, i}
		<div
			class="hero-slide absolute inset-0 bg-cover bg-center will-change-[opacity] transition-opacity duration-1000 ease-in-out"
			class:opacity-100={currentSlide === i}
			class:opacity-0={currentSlide !== i}
			style="background-image: url('{src}')"
		></div>
	{/each}
	<div class="absolute inset-0 bg-linear-to-t from-[rgba(0,0,0,0.7)] via-[rgba(0,0,0,0.3)] to-[rgba(0,0,0,0.15)] z-1"></div>

	<div class="container relative z-2 text-center pb-24">
		<h1 class="font-serif text-[clamp(2rem,5vw,3.5rem)] font-bold text-white mb-4 drop-shadow-[0_2px_20px_rgba(0,0,0,0.3)] tracking-tight">To Truly Know Jesus<br />And To Make His Truth Known.</h1>
		<p class="text-[clamp(1rem,2vw,1.35rem)] text-white/90 mb-8 font-normal tracking-[0.05em]">Sundays at 9:30AM and 11:00AM</p>
		<a href="https://fbcwimberley.com/watch/" class="btn btn-outline hover:btn-outline-hover">Watch Now</a>
	</div>
</section>

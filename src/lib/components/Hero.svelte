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

<section class="hero">
	{#each images as src, i}
		<div
			class="hero-slide"
			class:active={currentSlide === i}
			style="background-image: url('{src}')"
		></div>
	{/each}
	<div class="hero-overlay"></div>

	<div class="hero-content container">
		<h1 class="hero-title">To Truly Know Jesus<br />And To Make His Truth Known.</h1>
		<p class="hero-subtitle">Sundays at 9:30AM and 11:00AM</p>
		<a href="https://fbcwimberley.com/watch/" class="btn btn-outline">Watch Now</a>
	</div>
</section>

<style>
	.hero {
		position: relative;
		min-height: 100vh;
		display: flex;
		align-items: flex-end;
		justify-content: center;
		overflow: hidden;
	}

	.hero-slide {
		position: absolute;
		inset: 0;
		background-size: cover;
		background-position: center;
		opacity: 0;
		transition: opacity 1s ease-in-out;
		will-change: opacity;
	}

	.hero-slide.active {
		opacity: 1;
	}

	.hero-overlay {
		position: absolute;
		inset: 0;
		background: linear-gradient(
			to top,
			rgba(0, 0, 0, 0.7) 0%,
			rgba(0, 0, 0, 0.3) 50%,
			rgba(0, 0, 0, 0.15) 100%
		);
		z-index: 1;
	}

	.hero-content {
		position: relative;
		z-index: 2;
		text-align: center;
		padding-bottom: 6rem;
	}

	.hero-title {
		font-family: var(--font-serif);
		font-size: clamp(2rem, 5vw, 3.5rem);
		font-weight: 700;
		color: #ffffff;
		margin-bottom: 1rem;
		text-shadow: 0 2px 20px rgba(0, 0, 0, 0.3);
		letter-spacing: -0.01em;
	}

	.hero-subtitle {
		font-size: clamp(1rem, 2vw, 1.35rem);
		color: rgba(255, 255, 255, 0.9);
		margin-bottom: 2rem;
		font-weight: 400;
		letter-spacing: 0.05em;
	}
</style>

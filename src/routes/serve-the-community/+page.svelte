<script lang="ts">
	const communityCards = [
		{
			title: 'Carpenters Helpers',
			image: 'https://fbcwimberley.com/wp-content/uploads/2020/02/img-15.jpg',
			href: 'https://fbcwimberley.com/carpentershelpers/'
		}
	];
</script>

<svelte:head>
	<title>Serve The Community - First Baptist Church Wimberley</title>
</svelte:head>

<section class="relative min-h-screen flex items-center justify-center overflow-hidden bg-[#132638]">
	<div class="absolute inset-0 flex items-center justify-center">
		<img
			src="https://fbcwimberley.com/wp-content/uploads/2021/04/missions-2.jpeg"
			alt="Serve the community"
			loading="lazy"
			class="h-full w-auto object-contain"
		/>
	</div>
	<div class="absolute inset-0 bg-[linear-gradient(135deg,rgba(6,29,55,0.62),rgba(67,133,243,0.28))]"></div>
	<div class="relative z-1 text-center px-6 max-w-[900px]">
		<p class="section-label text-white/85">Serve</p>
		<h1 class="text-[clamp(2.4rem,6vw,4.4rem)] text-white leading-[1.02] mb-4">Serve</h1>
		<p class="text-[clamp(1.05rem,2.4vw,1.55rem)] leading-[1.5] text-white/90">
			Find Out How You Can Make A Difference
			<br />
			Serving from
			<br />
			our neighborhoods
			<br />
			to the nations.
		</p>
	</div>
</section>

<section class="py-18 md:py-22">
	<div class="container max-w-[1180px]">
		<div class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-3 gap-8 xl:gap-10">
			{#each communityCards as card}
				<article class="rounded-[var(--radius-lg)] overflow-hidden border border-(--color-border-light) bg-(--color-bg-card) shadow-(--shadow-sm)">
					<a href={card.href} target="_blank" rel="noopener">
						<img src={card.image} alt={card.title} loading="lazy" class="w-full h-[220px] md:h-[240px] object-cover" />
					</a>
					<div class="p-6">
						<h3 class="text-[1.35rem] mb-3">{card.title}</h3>
						<a href={card.href} target="_blank" rel="noopener" class="font-semibold text-(--color-primary) hover:text-(--color-primary-hover)">
							Find Out More
						</a>
					</div>
				</article>
			{/each}
		</div>
	</div>
</section>

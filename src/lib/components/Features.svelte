<script lang="ts">
	const features = [
		{
			icon: 'tv',
			title: 'Watch Online',
			description: 'Join us each Sunday for a live stream of our 11AM worship gathering or on-demand any time of the week!',
			href: 'https://fbcwimberley.com/watch/'
		},
		{
			icon: 'calendar',
			title: 'Upcoming Events',
			description: "There's always something happening in the life of our church. Check out all the upcoming events and registrations.",
			href: 'https://fbcwimberley.churchcenter.com/registrations'
		},
		{
			icon: 'users',
			title: 'Join A Group',
			description: 'Life is not meant to be lived alone! Find people who can help you grow in your desire to know Jesus.',
			href: 'https://fbcwimberley.churchcenter.com/groups'
		}
	];
</script>

<section class="features">
	<div class="features-bg" style="background-image: url('https://fbcwimberley.com/wp-content/uploads/2022/01/s-h-gue-CjMwAu4-OqY-unsplash-scaled.jpg')">
		<div class="features-overlay"></div>
	</div>

	<div class="features-content">
		<p class="features-label">Get Connected</p>
		<h2 class="features-heading">There's a place for you here.</h2>

		<div class="features-grid">
			{#each features as feature}
				<a href={feature.href} class="feature-card" target={feature.href.startsWith('https://fbcwimberley.com') ? undefined : '_blank'}>
					<div class="feature-icon">
						{#if feature.icon === 'tv'}
							<svg xmlns="http://www.w3.org/2000/svg" width="30" height="30" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="7" width="20" height="15" rx="2" ry="2"></rect><polyline points="17 2 12 7 7 2"></polyline></svg>
						{:else if feature.icon === 'calendar'}
							<svg xmlns="http://www.w3.org/2000/svg" width="30" height="30" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="4" width="18" height="18" rx="2" ry="2"></rect><line x1="16" y1="2" x2="16" y2="6"></line><line x1="8" y1="2" x2="8" y2="6"></line><line x1="3" y1="10" x2="21" y2="10"></line></svg>
						{:else}
							<svg xmlns="http://www.w3.org/2000/svg" width="30" height="30" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"></path><circle cx="9" cy="7" r="4"></circle><path d="M23 21v-2a4 4 0 0 0-3-3.87"></path><path d="M16 3.13a4 4 0 0 1 0 7.75"></path></svg>
						{/if}
					</div>
					<h3 class="feature-title">{feature.title}</h3>
					<p class="feature-desc">{feature.description}</p>
					<span class="feature-link">
						Learn more
						<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"></line><polyline points="12 5 19 12 12 19"></polyline></svg>
					</span>
				</a>
			{/each}
		</div>
	</div>
</section>

<style>
	.features {
		position: relative;
		padding: 5rem 0;
		overflow: hidden;
	}

	.features-bg {
		position: absolute;
		inset: 0;
		background-size: cover;
		background-position: center;
		background-attachment: fixed;
	}

	.features-overlay {
		position: absolute;
		inset: 0;
		background: linear-gradient(
			160deg,
			rgba(26, 26, 46, 0.93) 0%,
			rgba(26, 26, 46, 0.85) 50%,
			rgba(44, 95, 124, 0.80) 100%
		);
	}

	.features-content {
		position: relative;
		z-index: 1;
		max-width: 1200px;
		margin: 0 auto;
		padding: 0 1.5rem;
		text-align: center;
	}

	.features-label {
		font-size: 0.8rem;
		font-weight: 600;
		text-transform: uppercase;
		letter-spacing: 0.15em;
		color: var(--color-accent);
		margin-bottom: 0.75rem;
	}

	.features-heading {
		font-size: clamp(1.75rem, 4vw, 2.75rem);
		color: #ffffff;
		margin-bottom: 3rem;
	}

	.features-grid {
		display: grid;
		grid-template-columns: 1fr;
		gap: 1.25rem;
	}

	.feature-card {
		display: flex;
		flex-direction: column;
		align-items: center;
		text-align: center;
		gap: 1rem;
		padding: 2.5rem 2rem;
		background: rgba(255, 255, 255, 0.07);
		backdrop-filter: blur(12px);
		-webkit-backdrop-filter: blur(12px);
		border: 1px solid rgba(255, 255, 255, 0.12);
		border-radius: var(--radius-lg);
		transition: all 400ms cubic-bezier(0.23, 1, 0.32, 1);
		text-decoration: none;
	}

	.feature-card:hover {
		transform: translateY(-6px);
		background: rgba(255, 255, 255, 0.12);
		border-color: rgba(255, 255, 255, 0.25);
		box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
	}

	.feature-card:hover .feature-link {
		opacity: 1;
		transform: translateY(0);
	}

	.feature-card:hover .feature-link svg {
		transform: translateX(4px);
	}

	.feature-icon {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 64px;
		height: 64px;
		background: rgba(200, 145, 90, 0.15);
		color: var(--color-accent);
		border-radius: var(--radius-full);
		border: 1px solid rgba(200, 145, 90, 0.25);
	}

	.feature-title {
		font-family: var(--font-serif);
		font-size: 1.3rem;
		font-weight: 600;
		color: #ffffff;
	}

	.feature-desc {
		font-size: 0.95rem;
		color: rgba(255, 255, 255, 0.7);
		line-height: 1.65;
		max-width: 320px;
	}

	.feature-link {
		display: inline-flex;
		align-items: center;
		gap: 0.4rem;
		font-size: 0.85rem;
		font-weight: 600;
		color: var(--color-accent);
		letter-spacing: 0.03em;
		opacity: 0;
		transform: translateY(6px);
		transition: all 300ms ease;
		margin-top: 0.25rem;
	}

	.feature-link svg {
		transition: transform 300ms ease;
	}

	@media (min-width: 768px) {
		.features {
			padding: 7rem 0;
		}

		.features-grid {
			grid-template-columns: repeat(3, 1fr);
			gap: 1.5rem;
		}
	}

	@media (min-width: 1024px) {
		.features-grid {
			gap: 2rem;
		}

		.feature-card {
			padding: 3rem 2rem;
		}
	}
</style>

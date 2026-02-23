<section class="nextstep">
	<div class="nextstep-content">
		<p class="nextstep-label">Your Journey</p>
		<h2>Take Your Next Step.</h2>
		<p class="nextstep-desc">
			Whether you're new to FBCW and are ready to surrender your life to Jesus or you've been around a while and are looking to get more connected &mdash; we want to help you take your next step to discover and deepen a relationship with Jesus.
		</p>

		<div class="nextstep-images">
			<div class="nextstep-image-wrap">
				<img
					src="https://fbcwimberley.com/wp-content/uploads/2024/01/102A0963-scaled.jpg"
					alt="Church community"
					loading="lazy"
				/>
			</div>
			<div class="nextstep-image-wrap">
				<img
					src="https://fbcwimberley.com/wp-content/uploads/2024/01/102A6400-1-scaled.jpg"
					alt="Church fellowship"
					loading="lazy"
				/>
			</div>
		</div>

		<a href="https://fbcwimberley.com/connect/" class="nextstep-btn">
			Take Your Next Step
			<svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"></line><polyline points="12 5 19 12 12 19"></polyline></svg>
		</a>
	</div>
</section>

<style>
	.nextstep {
		position: relative;
		padding: 5rem 0;
		background: var(--color-bg-alt);
		overflow: hidden;
	}

	.nextstep-content {
		position: relative;
		z-index: 1;
		max-width: 900px;
		margin: 0 auto;
		padding: 0 1.5rem;
		text-align: center;
	}

	.nextstep-label {
		font-size: 0.8rem;
		font-weight: 600;
		text-transform: uppercase;
		letter-spacing: 0.15em;
		color: var(--color-accent);
		margin-bottom: 0.75rem;
	}

	.nextstep-content h2 {
		font-size: clamp(2rem, 4vw, 3rem);
		color: var(--color-heading);
		margin-bottom: 1.25rem;
	}

	.nextstep-desc {
		font-size: 1.05rem;
		color: var(--color-text-muted);
		line-height: 1.7;
		max-width: 680px;
		margin: 0 auto 3rem;
	}

	.nextstep-images {
		display: grid;
		grid-template-columns: 1fr;
		gap: 1rem;
		margin-bottom: 2.5rem;
	}

	.nextstep-image-wrap {
		border-radius: var(--radius-lg);
		overflow: hidden;
		position: relative;
	}

	.nextstep-image-wrap::after {
		content: '';
		position: absolute;
		inset: 0;
		background: linear-gradient(
			to top,
			rgba(26, 26, 46, 0.2) 0%,
			transparent 50%
		);
		pointer-events: none;
		transition: opacity 400ms ease;
	}

	.nextstep-image-wrap:hover::after {
		opacity: 0;
	}

	.nextstep-image-wrap img {
		width: 100%;
		height: 260px;
		object-fit: cover;
		transition: transform 600ms cubic-bezier(0.23, 1, 0.32, 1);
	}

	.nextstep-image-wrap:hover img {
		transform: scale(1.04);
	}

	.nextstep-btn {
		display: inline-flex;
		align-items: center;
		gap: 0.5rem;
		padding: 0.85rem 2.5rem;
		border-radius: var(--radius-full);
		background: var(--color-primary);
		color: #ffffff;
		font-weight: 600;
		font-size: 0.95rem;
		letter-spacing: 0.02em;
		transition: all 300ms cubic-bezier(0.23, 1, 0.32, 1);
		text-decoration: none;
	}

	.nextstep-btn:hover {
		background: var(--color-primary-hover);
		color: #ffffff;
		transform: translateY(-2px);
		box-shadow: 0 8px 24px rgba(44, 95, 124, 0.3);
	}

	.nextstep-btn:hover svg {
		transform: translateX(4px);
	}

	.nextstep-btn svg {
		transition: transform 300ms ease;
	}

	@media (min-width: 768px) {
		.nextstep {
			padding: 7rem 0;
		}

		.nextstep-images {
			grid-template-columns: 1fr 1fr;
			gap: 1.5rem;
		}

		.nextstep-image-wrap img {
			height: 340px;
		}
	}
</style>

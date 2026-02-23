<script lang="ts">
	let firstName = $state('');
	let lastName = $state('');
	let email = $state('');
	let submitted = $state(false);

	function handleSubmit(e: SubmitEvent) {
		e.preventDefault();
		// In production, this would submit to Mailchimp or another service
		submitted = true;
		setTimeout(() => {
			submitted = false;
			firstName = '';
			lastName = '';
			email = '';
		}, 3000);
	}
</script>

<section class="newsletter">
	<div class="newsletter-bg" style="background-image: url('https://fbcwimberley.com/wp-content/uploads/2025/07/102A6447-scaled.jpg')">
		<div class="newsletter-overlay"></div>
	</div>

	<div class="newsletter-content">
		<p class="newsletter-label">Stay In The Loop</p>
		<h2>Sign up for our newsletter here!</h2>
		<p class="newsletter-desc">Stay connected with what's happening at FBC Wimberley. Get weekly updates delivered straight to your inbox.</p>

		<div class="newsletter-card">
			<form class="newsletter-form" onsubmit={handleSubmit}>
				{#if submitted}
					<div class="success-message">
						<svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"></path><polyline points="22 4 12 14.01 9 11.01"></polyline></svg>
						<span>Thanks for signing up! We'll be in touch.</span>
					</div>
				{:else}
					<div class="form-row">
						<div class="form-group">
							<label for="fname">First Name</label>
							<input type="text" id="fname" bind:value={firstName} placeholder="Your first name" required />
						</div>
						<div class="form-group">
							<label for="lname">Last Name</label>
							<input type="text" id="lname" bind:value={lastName} placeholder="Your last name" required />
						</div>
						<div class="form-group form-group-email">
							<label for="email">Email address</label>
							<input type="email" id="email" bind:value={email} placeholder="Your email address" required />
						</div>
					</div>
					<button type="submit" class="newsletter-btn">
						Sign Up
						<svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"></line><polyline points="12 5 19 12 12 19"></polyline></svg>
					</button>
				{/if}
			</form>
		</div>
	</div>
</section>

<style>
	.newsletter {
		position: relative;
		padding: 5rem 0;
		overflow: hidden;
	}

	.newsletter-bg {
		position: absolute;
		inset: 0;
		background-size: cover;
		background-position: center;
		background-attachment: fixed;
	}

	.newsletter-overlay {
		position: absolute;
		inset: 0;
		background: linear-gradient(
			160deg,
			rgba(26, 26, 46, 0.93) 0%,
			rgba(26, 26, 46, 0.85) 50%,
			rgba(44, 95, 124, 0.80) 100%
		);
	}

	.newsletter-content {
		position: relative;
		z-index: 1;
		max-width: 680px;
		margin: 0 auto;
		padding: 0 1.5rem;
		text-align: center;
	}

	.newsletter-label {
		font-size: 0.8rem;
		font-weight: 600;
		text-transform: uppercase;
		letter-spacing: 0.15em;
		color: var(--color-accent);
		margin-bottom: 0.75rem;
	}

	.newsletter-content h2 {
		font-size: clamp(1.75rem, 4vw, 2.5rem);
		color: #ffffff;
		margin-bottom: 1rem;
	}

	.newsletter-desc {
		font-size: 1rem;
		color: rgba(255, 255, 255, 0.7);
		line-height: 1.65;
		margin-bottom: 2.5rem;
	}

	.newsletter-card {
		background: rgba(255, 255, 255, 0.07);
		backdrop-filter: blur(12px);
		-webkit-backdrop-filter: blur(12px);
		border: 1px solid rgba(255, 255, 255, 0.12);
		border-radius: var(--radius-lg);
		padding: 1.5rem;
		overflow: hidden;
	}

	.newsletter-form {
		display: flex;
		flex-direction: column;
		gap: 1.25rem;
	}

	.form-row {
		display: grid;
		grid-template-columns: 1fr;
		gap: 1rem;
	}

	.form-group {
		display: flex;
		flex-direction: column;
		gap: 0.35rem;
		text-align: left;
	}

	.form-group label {
		font-size: 0.8rem;
		font-weight: 500;
		color: rgba(255, 255, 255, 0.6);
		text-transform: uppercase;
		letter-spacing: 0.05em;
	}

	.form-group input {
		width: 100%;
		min-width: 0;
		padding: 0.85rem 1rem;
		border: 1px solid rgba(255, 255, 255, 0.15);
		border-radius: var(--radius-sm);
		background: rgba(255, 255, 255, 0.08);
		color: #ffffff;
		font-size: 1rem;
		transition: all var(--transition);
		-webkit-appearance: none;
		appearance: none;
	}

	.form-group input::placeholder {
		color: rgba(255, 255, 255, 0.35);
	}

	.form-group input:focus {
		outline: none;
		border-color: var(--color-accent);
		background: rgba(255, 255, 255, 0.12);
		box-shadow: 0 0 0 3px rgba(200, 145, 90, 0.15);
	}

	.newsletter-btn {
		display: inline-flex;
		align-items: center;
		justify-content: center;
		gap: 0.5rem;
		width: 100%;
		padding: 0.85rem 2rem;
		border-radius: var(--radius-full);
		background: var(--color-accent);
		color: #ffffff;
		font-weight: 600;
		font-size: 0.95rem;
		letter-spacing: 0.02em;
		border: none;
		cursor: pointer;
		transition: all 300ms cubic-bezier(0.23, 1, 0.32, 1);
	}

	.newsletter-btn:hover {
		background: var(--color-accent-hover);
		transform: translateY(-2px);
		box-shadow: 0 8px 24px rgba(200, 145, 90, 0.3);
	}

	.newsletter-btn:hover svg {
		transform: translateX(4px);
	}

	.newsletter-btn svg {
		transition: transform 300ms ease;
	}

	.success-message {
		display: flex;
		align-items: center;
		justify-content: center;
		gap: 0.75rem;
		padding: 1.5rem;
		background: rgba(16, 185, 129, 0.15);
		border: 1px solid rgba(16, 185, 129, 0.3);
		color: #6ee7b7;
		border-radius: var(--radius-md);
		font-weight: 500;
		font-size: 1rem;
	}

	@media (min-width: 768px) {
		.newsletter {
			padding: 7rem 0;
		}

		.newsletter-card {
			padding: 2rem;
		}

		.form-row {
			grid-template-columns: 1fr 1fr;
		}

		.form-group-email {
			grid-column: 1 / -1;
		}
	}
</style>

<section class="events-cta">
	<div class="events-cta-overlay"></div>
	<div class="events-cta-content container">
		<h2>Want to find out what's happening at FBC Wimberley?</h2>
		<div class="events-cta-buttons">
			<a href="https://fbcwimberley.churchcenter.com/registrations" class="btn btn-outline">
				Find Upcoming Events
			</a>
			<a href="http://eepurl.com/bUEnaz" class="btn btn-accent">
				Signup For Our Weekly Email Newsletter
			</a>
		</div>
	</div>
</section>

<style>
	.events-cta {
		position: relative;
		padding: 6rem 0;
		background-image: url('https://fbcwimberley.com/wp-content/uploads/2024/01/102A0963-scaled.jpg');
		background-size: cover;
		background-position: center;
		background-attachment: fixed;
	}

	.events-cta-overlay {
		position: absolute;
		inset: 0;
		background: linear-gradient(135deg, rgba(26, 26, 46, 0.92), rgba(44, 95, 124, 0.85));
	}

	.events-cta-content {
		position: relative;
		z-index: 1;
		text-align: center;
	}

	.events-cta-content h2 {
		font-size: clamp(1.5rem, 4vw, 2.5rem);
		color: #ffffff;
		margin-bottom: 2rem;
		max-width: 700px;
		margin-inline: auto;
	}

	.events-cta-buttons {
		display: flex;
		flex-direction: column;
		gap: 1rem;
		align-items: center;
	}

	@media (min-width: 640px) {
		.events-cta-buttons {
			flex-direction: row;
			justify-content: center;
		}
	}
</style>

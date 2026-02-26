<script lang="ts">
	let firstName = $state('');
	let lastName = $state('');
	let email = $state('');
	let submitted = $state(false);
	let submitting = $state(false);
	let errorMessage = $state('');

	async function handleSubmit(e: SubmitEvent) {
		e.preventDefault();
		submitted = false;
		errorMessage = '';
		submitting = true;

		try {
			const response = await fetch('/api/newsletter', {
				method: 'POST',
				headers: {
					'Content-Type': 'application/json'
				},
				body: JSON.stringify({
					firstName,
					lastName,
					email
				})
			});

			if (!response.ok) {
				const data = await response.json().catch(() => null);
				errorMessage = data?.error ?? 'Unable to subscribe right now. Please try again.';
				return;
			}

			submitted = true;
			firstName = '';
			lastName = '';
			email = '';

			setTimeout(() => {
				submitted = false;
			}, 3000);
		} catch {
			errorMessage = 'Unable to subscribe right now. Please try again.';
		} finally {
			submitting = false;
		}
	}
</script>

<section class="relative py-20 md:py-28 overflow-hidden">
	<div class="absolute inset-0 bg-cover bg-center bg-fixed" style="background-image: url('/images/remote/fbcwimberley.com-s-h-gue-CjMwAu4-OqY-unsplash-scaled-f09ccd30b3.webp')">
		<div class="dark-overlay"></div>
	</div>

	<div class="relative z-1 max-w-[680px] mx-auto px-6 text-center">
		<p class="section-label">Stay In The Loop</p>
		<h2 class="text-[clamp(1.75rem,4vw,2.5rem)] text-white mb-4">Sign up for our newsletter here!</h2>
		<p class="text-base text-white/70 leading-[1.65] mb-10">Stay connected with what's happening at FBC Wimberley. Get weekly updates delivered straight to your inbox.</p>

		<div class="glass-card p-6 md:p-8 overflow-hidden">
			<form class="flex flex-col gap-5" onsubmit={handleSubmit}>
				{#if submitted}
					<div class="flex items-center justify-center gap-3 p-6 bg-[rgba(16,185,129,0.15)] border border-[rgba(16,185,129,0.3)] text-[#6ee7b7] rounded-[var(--radius-md)] font-medium text-base">
						<svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"></path><polyline points="22 4 12 14.01 9 11.01"></polyline></svg>
						<span>Thanks for signing up! We'll be in touch.</span>
					</div>
				{:else}
					{#if errorMessage}
						<div class="p-4 bg-[rgba(239,68,68,0.12)] border border-[rgba(239,68,68,0.35)] text-[#fecaca] rounded-[var(--radius-md)] text-sm text-left">
							{errorMessage}
						</div>
					{/if}
					<div class="grid grid-cols-1 md:grid-cols-2 gap-4">
						<div class="flex flex-col gap-1.5 text-left">
							<label for="fname" class="text-[0.8rem] font-medium text-white/60 uppercase tracking-[0.05em]">First Name</label>
							<input type="text" id="fname" bind:value={firstName} placeholder="Your first name" required class="w-full min-w-0 py-3.5 px-4 border border-white/15 rounded-[var(--radius-sm)] bg-white/8 text-white text-base transition-all duration-200 appearance-none placeholder:text-white/35 focus:outline-none focus:border-(--color-accent) focus:bg-white/12 focus:shadow-[0_0_0_3px_rgba(200,145,90,0.15)]" disabled={submitting} />
						</div>
						<div class="flex flex-col gap-1.5 text-left">
							<label for="lname" class="text-[0.8rem] font-medium text-white/60 uppercase tracking-[0.05em]">Last Name</label>
							<input type="text" id="lname" bind:value={lastName} placeholder="Your last name" required class="w-full min-w-0 py-3.5 px-4 border border-white/15 rounded-[var(--radius-sm)] bg-white/8 text-white text-base transition-all duration-200 appearance-none placeholder:text-white/35 focus:outline-none focus:border-(--color-accent) focus:bg-white/12 focus:shadow-[0_0_0_3px_rgba(200,145,90,0.15)]" disabled={submitting} />
						</div>
						<div class="flex flex-col gap-1.5 text-left md:col-span-2">
							<label for="email" class="text-[0.8rem] font-medium text-white/60 uppercase tracking-[0.05em]">Email address</label>
							<input type="email" id="email" bind:value={email} placeholder="Your email address" required class="w-full min-w-0 py-3.5 px-4 border border-white/15 rounded-[var(--radius-sm)] bg-white/8 text-white text-base transition-all duration-200 appearance-none placeholder:text-white/35 focus:outline-none focus:border-(--color-accent) focus:bg-white/12 focus:shadow-[0_0_0_3px_rgba(200,145,90,0.15)]" disabled={submitting} />
						</div>
					</div>
					<button type="submit" class="newsletter-btn inline-flex items-center justify-center gap-2 w-full py-3.5 px-8 rounded-full bg-(--color-accent) text-white font-semibold text-[0.95rem] tracking-[0.02em] border-none cursor-pointer transition-all duration-300 ease-[cubic-bezier(0.23,1,0.32,1)] hover:bg-(--color-accent-hover) hover:-translate-y-0.5 hover:shadow-[0_8px_24px_rgba(200,145,90,0.3)] disabled:opacity-70 disabled:cursor-not-allowed disabled:translate-y-0 disabled:shadow-none" disabled={submitting}>
						{submitting ? 'Signing Up...' : 'Sign Up'}
						<svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="transition-transform duration-300"><line x1="5" y1="12" x2="19" y2="12"></line><polyline points="12 5 19 12 12 19"></polyline></svg>
					</button>
				{/if}
			</form>
		</div>
	</div>
</section>

<style>
	.newsletter-btn:hover svg {
		transform: translateX(4px);
	}
</style>

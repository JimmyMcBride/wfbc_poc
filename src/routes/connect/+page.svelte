<script lang="ts">
	const ajaxEndpoint = 'https://fbcwimberley.com/wp-admin/admin-ajax.php';
	const elementorFormConfig = {
		action: 'elementor_pro_forms_send_form',
		postId: '4190',
		formId: '4d024a8d',
		refererTitle: 'Connect',
		queriedId: '4175',
		referrer: 'https://fbcwimberley.com/connect/'
	};

	const nextStepOptions = [
		'I Want To Follow Jesus',
		'I Want To Get Baptized',
		'I Want To Become A Member'
	];

	let name = $state('');
	let email = $state('');
	let phone = $state('');
	let selectedOptions = $state<string[]>([]);
	let submitting = $state(false);
	let submitted = $state(false);
	let submitError = $state('');
	let showOptionError = $state(false);

	function toggleOption(option: string) {
		if (selectedOptions.includes(option)) {
			selectedOptions = selectedOptions.filter((item) => item !== option);
			return;
		}
		selectedOptions = [...selectedOptions, option];
	}

	async function handleSubmit(e: SubmitEvent) {
		e.preventDefault();
		if (submitting) return;

		if (selectedOptions.length === 0) {
			showOptionError = true;
			return;
		}

		showOptionError = false;
		submitError = '';
		submitting = true;

		const formData = new FormData();
		formData.append('post_id', elementorFormConfig.postId);
		formData.append('form_id', elementorFormConfig.formId);
		formData.append('referer_title', elementorFormConfig.refererTitle);
		formData.append('queried_id', elementorFormConfig.queriedId);
		formData.append('form_fields[name]', name);
		formData.append('form_fields[email]', email);
		formData.append('form_fields[field_c7f1ab6]', phone);
		selectedOptions.forEach((option) => formData.append('form_fields[field_02876a0][]', option));
		formData.append('action', elementorFormConfig.action);
		formData.append('referrer', elementorFormConfig.referrer);

		try {
			const response = await fetch(ajaxEndpoint, {
				method: 'POST',
				body: formData,
				mode: 'no-cors'
			});

			// no-cors responses are opaque in the browser; treat that as a sent request
			if (response.type === 'opaque' || response.ok) {
				submitted = true;
				setTimeout(() => {
					submitted = false;
					name = '';
					email = '';
					phone = '';
					selectedOptions = [];
				}, 3500);
			} else {
				submitError = 'We could not send your request. Please try again.';
			}
		} catch {
			submitError = 'We could not send your request. Please try again.';
		} finally {
			submitting = false;
		}
	}
</script>

<svelte:head>
	<title>Connect - First Baptist Church Wimberley</title>
</svelte:head>

<section class="relative min-h-[52vh] md:min-h-[58vh] flex items-end justify-center overflow-hidden">
	<div class="absolute inset-0 bg-cover bg-center" style="background-image: url('/images/remote/fbcwimberley.com-102A5443-scaled-9aa360e309-1600.webp')"></div>
	<div class="absolute inset-0 bg-linear-to-t from-[rgba(0,0,0,0.72)] to-[rgba(0,0,0,0.25)]"></div>
	<div class="relative z-1 text-center pb-16 px-6">
		<p class="section-label">Get Connected</p>
		<h1 class="text-[clamp(2.4rem,6vw,4rem)] text-white drop-shadow-[0_2px_20px_rgba(0,0,0,0.3)]">Connect</h1>
		<p class="text-white/85 text-[1.02rem] max-w-[720px] mt-4">
			Wherever you are in your faith journey, we want to help you take your next step.
		</p>
	</div>
</section>

<section class="py-20 bg-(--color-bg-alt)">
	<div class="container">
		<div class="text-center mb-12">
			<p class="section-label">Start Here</p>
			<h2 class="text-[clamp(1.75rem,4vw,2.5rem)] mb-4">Ways To Connect</h2>
			<p class="text-(--color-text-muted) text-[1.02rem] leading-[1.75] max-w-[760px] mx-auto">
				New to FBC Wimberley? Looking for community? Ready to support what God is doing here? Use these quick links to jump in.
			</p>
		</div>

		<div class="grid grid-cols-1 md:grid-cols-3 gap-5">
			<a href="/about-us" class="connect-card p-7 rounded-[var(--radius-lg)] border border-(--color-border-light) bg-(--color-bg-card)">
				<p class="section-label mb-3">New Here?</p>
				<h3 class="text-[1.25rem] mb-2">Sunday Mornings</h3>
				<p class="text-(--color-text-muted) leading-[1.7] mb-5">Join us in person at 9:30AM and 11:00AM. We would love to meet you.</p>
				<span class="inline-flex items-center gap-2 font-semibold text-(--color-primary)">
					Plan Your Visit
					<svg xmlns="http://www.w3.org/2000/svg" width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"></line><polyline points="12 5 19 12 12 19"></polyline></svg>
				</span>
			</a>

			<a href="https://fbcwimberley.churchcenter.com/groups/" target="_blank" rel="noopener" class="connect-card p-7 rounded-[var(--radius-lg)] border border-(--color-border-light) bg-(--color-bg-card)">
				<p class="section-label mb-3">Get Plugged In</p>
				<h3 class="text-[1.25rem] mb-2">Join A Group</h3>
				<p class="text-(--color-text-muted) leading-[1.7] mb-5">Find people to grow with through Bible studies, classes, and ministry groups.</p>
				<span class="inline-flex items-center gap-2 font-semibold text-(--color-primary)">
					Browse Groups
					<svg xmlns="http://www.w3.org/2000/svg" width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"></line><polyline points="12 5 19 12 12 19"></polyline></svg>
				</span>
			</a>

			<a href="https://onrealm.org/fbcwimberley/give/now" target="_blank" rel="noopener" class="connect-card p-7 rounded-[var(--radius-lg)] border border-(--color-border-light) bg-(--color-bg-card)">
				<p class="section-label mb-3">Support The Mission</p>
				<h3 class="text-[1.25rem] mb-2">Give Online</h3>
				<p class="text-(--color-text-muted) leading-[1.7] mb-5">Would you like to give to what God is doing at FBCW? Give securely online.</p>
				<span class="inline-flex items-center gap-2 font-semibold text-(--color-primary)">
					Give Now
					<svg xmlns="http://www.w3.org/2000/svg" width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"></line><polyline points="12 5 19 12 12 19"></polyline></svg>
				</span>
			</a>
		</div>
	</div>
</section>

<section class="relative py-24 md:py-28 overflow-hidden">
	<div class="absolute inset-0 bg-cover bg-center bg-fixed" style="background-image: url('/images/remote/fbcwimberley.com-102A6400-1-scaled-2a1dd8d246-960.webp')">
		<div class="dark-overlay"></div>
	</div>

	<div class="relative z-1 container max-w-[900px] text-center">
		<p class="section-label">Take Your Next Step</p>
		<h2 class="text-[clamp(1.8rem,4vw,2.7rem)] text-white mb-4">Take Your Next Step!</h2>
		<p class="text-white/78 text-[1.02rem] leading-[1.75] max-w-[760px] mx-auto mb-10">
			We want to help you take your next step at FBC Wimberley. We can help you with these options and more.
		</p>

		<div class="glass-card p-6 md:p-9 text-left">
			<form class="flex flex-col gap-5" onsubmit={handleSubmit}>
				{#if submitted}
					<div class="flex items-center gap-3 rounded-[var(--radius-md)] border border-[rgba(16,185,129,0.3)] bg-[rgba(16,185,129,0.15)] text-[#6ee7b7] p-5">
						<svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"></path><polyline points="22 4 12 14.01 9 11.01"></polyline></svg>
						<p class="font-medium">Thanks for reaching out. A member of our team will follow up soon.</p>
					</div>
				{:else}
					<div class="grid grid-cols-1 md:grid-cols-2 gap-4">
						<div class="flex flex-col gap-1.5 md:col-span-2">
							<label for="name" class="text-[0.8rem] font-medium text-white/65 uppercase tracking-[0.06em]">Name</label>
							<input id="name" type="text" bind:value={name} required placeholder="Your name" class="form-input" />
						</div>
						<div class="flex flex-col gap-1.5">
							<label for="email" class="text-[0.8rem] font-medium text-white/65 uppercase tracking-[0.06em]">Email</label>
							<input id="email" type="email" bind:value={email} required placeholder="you@email.com" class="form-input" />
						</div>
						<div class="flex flex-col gap-1.5">
							<label for="phone" class="text-[0.8rem] font-medium text-white/65 uppercase tracking-[0.06em]">Phone Number</label>
							<input id="phone" type="tel" bind:value={phone} placeholder="(555) 555-5555" class="form-input" />
						</div>
					</div>

					<div>
						<p class="text-[0.8rem] font-medium text-white/65 uppercase tracking-[0.06em] mb-3">How can we help?</p>
						<div class="grid grid-cols-1 sm:grid-cols-2 gap-2.5">
							{#each nextStepOptions as option}
								<button
									type="button"
									onclick={() => toggleOption(option)}
									class="option-chip text-left py-2.5 px-3.5 rounded-[var(--radius-sm)] border border-white/14 bg-white/6 text-white/82 text-[0.92rem] transition-all duration-200 hover:border-(--color-accent) hover:text-white"
									class:selected={selectedOptions.includes(option)}
								>
									{option}
								</button>
							{/each}
						</div>
						{#if showOptionError}
							<p class="text-[#fca5a5] text-[0.86rem] mt-2.5">Please choose at least one option.</p>
						{/if}
					</div>

					<div class="pt-2">
						<button type="submit" class="nextstep-submit inline-flex items-center justify-center gap-2 py-3.5 px-8 rounded-full bg-(--color-accent) text-white font-semibold text-[0.95rem] tracking-[0.02em] transition-all duration-300 ease-[cubic-bezier(0.23,1,0.32,1)] hover:bg-(--color-accent-hover) hover:-translate-y-0.5 hover:shadow-[0_8px_24px_rgba(200,145,90,0.3)] disabled:opacity-70 disabled:cursor-not-allowed disabled:transform-none disabled:shadow-none" disabled={submitting}>
							{submitting ? 'Sending...' : 'Take My Next Step'}
							<svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="transition-transform duration-300"><line x1="5" y1="12" x2="19" y2="12"></line><polyline points="12 5 19 12 12 19"></polyline></svg>
						</button>
						{#if submitError}
							<p class="text-[#fca5a5] text-[0.86rem] mt-2.5">{submitError}</p>
						{/if}
					</div>
				{/if}
			</form>
		</div>
	</div>
</section>

<section class="py-20">
	<div class="container max-w-[760px] text-center">
		<p class="section-label">Need Help?</p>
		<h2 class="text-[clamp(1.75rem,4vw,2.4rem)] mb-4">Want To Ask More Questions? Let's Connect.</h2>
		<p class="text-(--color-text-muted) text-[1.02rem] leading-[1.75] mb-8">
			If you would rather talk with someone directly, our team is ready to help.
		</p>

		<div class="flex flex-wrap justify-center gap-3.5 mb-6">
			<a href="mailto:office@fbcwimberley.com" class="btn btn-outline-dark hover:btn-outline-dark-hover">Email Us</a>
			<a href="tel:+15128479035" class="btn btn-outline-dark hover:btn-outline-dark-hover">Call 512-847-9035</a>
		</div>

		<div class="flex flex-wrap items-center justify-center gap-3">
			<a href="https://www.facebook.com/firstwimberley" target="_blank" rel="noopener" class="social-pill">Facebook</a>
			<a href="https://www.instagram.com/fbc_wimberley/" target="_blank" rel="noopener" class="social-pill">Instagram</a>
			<a href="https://www.youtube.com/channel/UCBR1Vcq5wc2L6QFa9U2FTJw" target="_blank" rel="noopener" class="social-pill">YouTube</a>
		</div>
	</div>
</section>

<style>
	.connect-card {
		transition: transform 260ms ease, box-shadow 260ms ease, border-color 260ms ease;
	}

	.connect-card:hover {
		transform: translateY(-4px);
		box-shadow: var(--shadow-md);
		border-color: var(--color-border);
	}

	.connect-card:hover svg {
		transform: translateX(4px);
	}

	.connect-card svg {
		transition: transform 220ms ease;
	}

	.form-input {
		width: 100%;
		min-width: 0;
		padding: 0.85rem 1rem;
		border: 1px solid rgba(255, 255, 255, 0.15);
		border-radius: var(--radius-sm);
		background: rgba(255, 255, 255, 0.08);
		color: white;
		font-size: 1rem;
		transition: all 200ms ease;
		appearance: none;
	}

	.form-input::placeholder {
		color: rgba(255, 255, 255, 0.4);
	}

	.form-input:focus {
		outline: none;
		border-color: var(--color-accent);
		background: rgba(255, 255, 255, 0.12);
		box-shadow: 0 0 0 3px rgba(200, 145, 90, 0.15);
	}

	.option-chip.selected {
		border-color: var(--color-accent);
		background: rgba(200, 145, 90, 0.18);
		color: white;
	}

	.nextstep-submit:hover svg {
		transform: translateX(4px);
	}

	.social-pill {
		display: inline-flex;
		align-items: center;
		justify-content: center;
		padding: 0.5rem 1rem;
		border-radius: var(--radius-full);
		border: 1px solid var(--color-border);
		background: var(--color-bg-card);
		color: var(--color-text-muted);
		font-size: 0.9rem;
		transition: all 200ms ease;
	}

	.social-pill:hover {
		color: var(--color-primary);
		border-color: var(--color-primary);
		transform: translateY(-1px);
	}
</style>

<script lang="ts">
	import ThemeToggle from './ThemeToggle.svelte';

	let mobileMenuOpen = $state(false);
	let ministriesOpen = $state(false);
	let familyLifeOpen = $state(false);
	let serveOpen = $state(false);
	let scrolled = $state(false);

	function handleScroll() {
		scrolled = window.scrollY > 50;
	}

	function closeMobile() {
		mobileMenuOpen = false;
		ministriesOpen = false;
		familyLifeOpen = false;
		serveOpen = false;
	}
</script>

<svelte:window onscroll={handleScroll} />

<header class="header" class:scrolled>
	<div class="header-inner container">
		<a href="/" class="logo">
			<img
				src="https://fbcwimberley.com/wp-content/uploads/2022/09/First-Baptist-Church-of-wimberley-Wordmark-black.png"
				alt="First Baptist Church Wimberley"
				class="logo-img logo-light"
			/>
			<img
				src="https://fbcwimberley.com/wp-content/uploads/2022/09/First-Baptist-Church-of-wimberley-Wordmark-white-2.png"
				alt="First Baptist Church Wimberley"
				class="logo-img logo-dark"
			/>
		</a>

		<nav class="desktop-nav">
			<ul class="nav-list">
				<li><a href="/about-us">About Us</a></li>
				<li class="has-dropdown">
					<button class="nav-link" onclick={() => ministriesOpen = !ministriesOpen}>
						Ministries
						<svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"></polyline></svg>
					</button>
					<ul class="dropdown">
						<li><a href="https://fbcwimberley.com/womens-ministry/">Women's Ministry</a></li>
						<li><a href="https://fbcwimberley.churchcenter.com/groups/ministries-fbcw/widows-ministry">Widows Ministry</a></li>
						<li><a href="https://fbcwimberley.churchcenter.com/groups/ministries-fbcw/men-s-ministry">Men's Ministry</a></li>
						<li><a href="https://fbcwimberley.com/care/">Care</a></li>
						<li><a href="https://www.youtube.com/playlist?list=PLKz_XG7H0s7ph34R0pZLEF55wfrM34kyo">Missions</a></li>
						<li class="has-subdropdown">
							<span class="subdropdown-label">
								Family Life
								<svg xmlns="http://www.w3.org/2000/svg" width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="9 18 15 12 9 6"></polyline></svg>
							</span>
							<ul class="subdropdown">
								<li><a href="https://fbcwimberley.com/preschool/">Preschool</a></li>
								<li><a href="https://fbcwimberley.com/elementary/">Elementary</a></li>
								<li><a href="https://fbcwimberley.com/junior-high/">Junior High</a></li>
								<li><a href="https://fbcwimberley.com/high-school/">High School</a></li>
								<li><a href="https://fbcwimberley.com/kids-day-out/">Kids Day Out</a></li>
							</ul>
						</li>
					</ul>
				</li>
				<li><a href="https://fbcwimberley.churchcenter.com/groups/">Groups</a></li>
				<li class="has-dropdown">
					<button class="nav-link" onclick={() => serveOpen = !serveOpen}>
						Serve
						<svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"></polyline></svg>
					</button>
					<ul class="dropdown">
						<li><a href="https://fbcwimberley.com/servethechurch/">Serve The Church</a></li>
						<li><a href="https://fbcwimberley.com/serve-the-community/">Serve The Community</a></li>
					</ul>
				</li>
				<li><a href="https://fbcwimberley.churchcenter.com/registrations">Events</a></li>
				<li>
					<a href="https://onrealm.org/fbcwimberley/give/now" target="_blank" class="btn btn-accent">Give</a>
				</li>
			</ul>
		</nav>

		<div class="header-actions">
			<ThemeToggle />
			<button
				class="mobile-toggle"
				onclick={() => mobileMenuOpen = !mobileMenuOpen}
				aria-label="Toggle menu"
				aria-expanded={mobileMenuOpen}
			>
				{#if mobileMenuOpen}
					<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="18" y1="6" x2="6" y2="18"></line><line x1="6" y1="6" x2="18" y2="18"></line></svg>
				{:else}
					<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="3" y1="12" x2="21" y2="12"></line><line x1="3" y1="6" x2="21" y2="6"></line><line x1="3" y1="18" x2="21" y2="18"></line></svg>
				{/if}
			</button>
		</div>
	</div>

	<!-- Mobile Menu -->
	{#if mobileMenuOpen}
		<div class="mobile-overlay" onclick={closeMobile} role="presentation"></div>
		<nav class="mobile-nav">
			<ul class="mobile-nav-list">
				<li><a href="/about-us" onclick={closeMobile}>About Us</a></li>
				<li>
					<button class="mobile-accordion" onclick={() => ministriesOpen = !ministriesOpen}>
						Ministries
						<svg class:rotated={ministriesOpen} xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"></polyline></svg>
					</button>
					{#if ministriesOpen}
						<ul class="mobile-sub">
							<li><a href="https://fbcwimberley.com/womens-ministry/" onclick={closeMobile}>Women's Ministry</a></li>
							<li><a href="https://fbcwimberley.churchcenter.com/groups/ministries-fbcw/widows-ministry" onclick={closeMobile}>Widows Ministry</a></li>
							<li><a href="https://fbcwimberley.churchcenter.com/groups/ministries-fbcw/men-s-ministry" onclick={closeMobile}>Men's Ministry</a></li>
							<li><a href="https://fbcwimberley.com/care/" onclick={closeMobile}>Care</a></li>
							<li><a href="https://www.youtube.com/playlist?list=PLKz_XG7H0s7ph34R0pZLEF55wfrM34kyo" onclick={closeMobile}>Missions</a></li>
							<li>
								<button class="mobile-accordion sub" onclick={() => familyLifeOpen = !familyLifeOpen}>
									Family Life
									<svg class:rotated={familyLifeOpen} xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"></polyline></svg>
								</button>
								{#if familyLifeOpen}
									<ul class="mobile-sub nested">
										<li><a href="https://fbcwimberley.com/preschool/" onclick={closeMobile}>Preschool</a></li>
										<li><a href="https://fbcwimberley.com/elementary/" onclick={closeMobile}>Elementary</a></li>
										<li><a href="https://fbcwimberley.com/junior-high/" onclick={closeMobile}>Junior High</a></li>
										<li><a href="https://fbcwimberley.com/high-school/" onclick={closeMobile}>High School</a></li>
										<li><a href="https://fbcwimberley.com/kids-day-out/" onclick={closeMobile}>Kids Day Out</a></li>
									</ul>
								{/if}
							</li>
						</ul>
					{/if}
				</li>
				<li><a href="https://fbcwimberley.churchcenter.com/groups/" onclick={closeMobile}>Groups</a></li>
				<li>
					<button class="mobile-accordion" onclick={() => serveOpen = !serveOpen}>
						Serve
						<svg class:rotated={serveOpen} xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"></polyline></svg>
					</button>
					{#if serveOpen}
						<ul class="mobile-sub">
							<li><a href="https://fbcwimberley.com/servethechurch/" onclick={closeMobile}>Serve The Church</a></li>
							<li><a href="https://fbcwimberley.com/serve-the-community/" onclick={closeMobile}>Serve The Community</a></li>
						</ul>
					{/if}
				</li>
				<li><a href="https://fbcwimberley.churchcenter.com/registrations" onclick={closeMobile}>Events</a></li>
				<li class="mobile-give">
					<a href="https://onrealm.org/fbcwimberley/give/now" target="_blank" class="btn btn-accent" onclick={closeMobile}>Give</a>
				</li>
			</ul>
		</nav>
	{/if}
</header>

<style>
	.header {
		position: fixed;
		top: 0;
		left: 0;
		right: 0;
		z-index: 100;
		background: transparent;
		transition: all 300ms ease;
	}

	.header.scrolled {
		background: var(--color-bg);
		box-shadow: var(--shadow-md);
	}

	.header-inner {
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding-top: 1rem;
		padding-bottom: 1rem;
	}

	.logo {
		flex-shrink: 0;
	}

	.logo-img {
		height: 40px;
		width: auto;
	}

	/* Show white logo when not scrolled, dark logo when scrolled */
	.logo-light {
		display: none;
	}
	.logo-dark {
		display: block;
	}

	.header.scrolled .logo-light {
		display: block;
	}
	.header.scrolled .logo-dark {
		display: none;
	}

	/* In dark mode, always show white logo */
	:global(.dark) .logo-light {
		display: none !important;
	}
	:global(.dark) .logo-dark {
		display: block !important;
	}

	.desktop-nav {
		display: none;
	}

	.nav-list {
		display: flex;
		align-items: center;
		gap: 0.25rem;
	}

	.nav-list > li > a,
	.nav-link {
		display: inline-flex;
		align-items: center;
		gap: 0.3rem;
		padding: 0.5rem 0.85rem;
		font-size: 0.9rem;
		font-weight: 500;
		color: var(--color-text-inverse);
		border-radius: var(--radius-sm);
		transition: all var(--transition);
	}

	.header.scrolled .nav-list > li > a,
	.header.scrolled .nav-link {
		color: var(--color-nav-text);
	}

	.nav-list > li > a:hover,
	.nav-link:hover {
		color: var(--color-accent);
	}

	.nav-list > li > a.btn {
		color: var(--color-text-inverse);
		padding: 0.5rem 1.5rem;
		font-size: 0.85rem;
	}

	/* Dropdowns */
	.has-dropdown {
		position: relative;
	}

	.dropdown {
		display: none;
		position: absolute;
		top: 100%;
		left: 0;
		min-width: 220px;
		background: var(--color-bg-card);
		border: 1px solid var(--color-border);
		border-radius: var(--radius-md);
		box-shadow: var(--shadow-lg);
		padding: 0.5rem;
		z-index: 50;
	}

	.has-dropdown:hover .dropdown {
		display: block;
	}

	.dropdown li a,
	.subdropdown-label {
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: 0.6rem 0.85rem;
		font-size: 0.875rem;
		color: var(--color-text);
		border-radius: var(--radius-sm);
		transition: all var(--transition);
	}

	.dropdown li a:hover {
		background: var(--color-primary-light);
		color: var(--color-primary);
	}

	.subdropdown-label {
		cursor: default;
		font-weight: 500;
	}

	/* Sub-dropdown */
	.has-subdropdown {
		position: relative;
	}

	.subdropdown {
		display: none;
		position: absolute;
		top: 0;
		left: 100%;
		min-width: 200px;
		background: var(--color-bg-card);
		border: 1px solid var(--color-border);
		border-radius: var(--radius-md);
		box-shadow: var(--shadow-lg);
		padding: 0.5rem;
	}

	.has-subdropdown:hover .subdropdown {
		display: block;
	}

	/* Header actions */
	.header-actions {
		display: flex;
		align-items: center;
		gap: 0.75rem;
	}

	.mobile-toggle {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 40px;
		height: 40px;
		color: var(--color-text-inverse);
		border-radius: var(--radius-sm);
		transition: all var(--transition);
	}

	.header.scrolled .mobile-toggle {
		color: var(--color-nav-text);
	}

	:global(.dark) .mobile-toggle {
		color: var(--color-nav-text);
	}

	/* Mobile nav */
	.mobile-overlay {
		position: fixed;
		inset: 0;
		background: rgba(0, 0, 0, 0.5);
		z-index: 90;
	}

	.mobile-nav {
		position: fixed;
		top: 0;
		right: 0;
		bottom: 0;
		width: min(320px, 85vw);
		background: var(--color-bg);
		z-index: 95;
		padding: 5rem 1.5rem 2rem;
		overflow-y: auto;
		box-shadow: var(--shadow-lg);
	}

	.mobile-nav-list > li > a,
	.mobile-accordion {
		display: flex;
		align-items: center;
		justify-content: space-between;
		width: 100%;
		padding: 0.85rem 0;
		font-size: 1rem;
		font-weight: 500;
		color: var(--color-text);
		border-bottom: 1px solid var(--color-border-light);
		transition: color var(--transition);
	}

	.mobile-accordion {
		text-align: left;
	}

	.mobile-accordion svg {
		transition: transform 200ms ease;
	}

	.mobile-accordion svg.rotated {
		transform: rotate(180deg);
	}

	.mobile-sub {
		padding-left: 1rem;
	}

	.mobile-sub li a {
		display: block;
		padding: 0.6rem 0;
		font-size: 0.9rem;
		color: var(--color-text-muted);
		border-bottom: 1px solid var(--color-border-light);
	}

	.mobile-sub li a:hover {
		color: var(--color-primary);
	}

	.mobile-accordion.sub {
		font-size: 0.9rem;
		font-weight: 400;
		color: var(--color-text-muted);
	}

	.mobile-sub.nested {
		padding-left: 0.75rem;
	}

	.mobile-give {
		padding-top: 1rem;
	}

	.mobile-give .btn {
		width: 100%;
		justify-content: center;
	}

	@media (min-width: 1024px) {
		.desktop-nav {
			display: block;
		}
		.mobile-toggle {
			display: none;
		}
	}
</style>

<script lang="ts">
	const staff = [
		{
			name: 'Dr. Aaron T. Colyer',
			title: 'Lead Pastor, Elder',
			email: 'pastoraaron@fbcwimberley.com',
			image: 'https://fbcwimberley.com/wp-content/uploads/2026/01/Aaron-Colyer-1024x683.jpg',
			bio: 'Aaron and his sweet bride Krista married in 2006. They have three amazing kids. He has a passion for equipping the saints for the work of ministry and a desire to see all believers take the gospel to the ends of the earth. This includes a focus on family discipleship and making Christ the center of every home. Born and raised in Texas, he received a B.S. in Communications from the University of Texas in Austin, his M.Div. and Doctorate in Leadership from The Southern Baptist Theological Seminary. Outside of ministry you can find Aaron enjoying family time and spending as much time as possible outdoors.'
		},
		{
			name: 'Mike Gibbons',
			title: 'Executive Pastor',
			email: 'mike@fbcwimberley.com',
			image: 'https://fbcwimberley.com/wp-content/uploads/2026/01/Mike-Gibbons-1024x683.jpg'
		},
		{
			name: 'Isak Morehous',
			title: 'Minister to Students and Families',
			email: 'isak@fbcwimberley.com',
			image: 'https://fbcwimberley.com/wp-content/uploads/2026/01/Isak-Morehous-1024x683.jpg'
		},
		{
			name: 'Dan Stephens',
			title: 'Minister to Senior Adults',
			email: 'dan@fbcwimberley.com',
			image: 'https://fbcwimberley.com/wp-content/uploads/2026/01/Dan-Stephens-1024x683.jpg'
		},
		{
			name: 'Melinda Tyler',
			title: 'Ministry Director to Kids and Families',
			email: 'melinda@fbcwimberley.com',
			image: 'https://fbcwimberley.com/wp-content/uploads/2026/01/Melinda-Tyler-1024x683.jpg'
		},
		{
			name: 'Nancy Williams',
			title: 'Life Coach and Consultant',
			email: 'nancy@fbcwimberley.com',
			image: 'https://fbcwimberley.com/wp-content/uploads/2026/01/Nancy-Williams-1024x683.jpg'
		},
		{
			name: 'Jake Kral',
			title: 'Minister Of Music and Creative Arts',
			email: 'music@fbcwimberley.com',
			image: 'https://fbcwimberley.com/wp-content/uploads/2026/01/Jake-Kral-1024x683.jpg'
		},
		{
			name: 'Marty Beard',
			title: 'Church Administrative Professional',
			email: 'marty@fbcwimberley.com',
			image: 'https://fbcwimberley.com/wp-content/uploads/2026/01/Marty-Beard-1024x683.jpg'
		},
		{
			name: 'Steve Youngblood',
			title: 'Facilities Assistant',
			email: 'office@fbcwimberley.com',
			image: 'https://fbcwimberley.com/wp-content/uploads/2026/01/Steve-Youngblood-1024x683.jpg'
		},
		{
			name: 'Shelby Hubbard',
			title: "Kid's Day Out Director",
			email: 'shelby@fbcwimberley.com',
			image: 'https://fbcwimberley.com/wp-content/uploads/2026/01/Shelby-Hubbard-1024x683.jpg'
		},
		{
			name: 'Shannon Tyson',
			title: 'Finance',
			email: 'financial@fbcwimberley.com',
			image: 'https://fbcwimberley.com/wp-content/uploads/2026/01/Your-paragraph-text-2-1024x683.png'
		},
		{
			name: 'John Dunn',
			title: 'Elder',
			image: 'https://fbcwimberley.com/wp-content/uploads/2026/01/John-Dunn-1024x683.jpg'
		},
		{
			name: 'Mike Stevens',
			title: 'Elder',
			image: 'https://fbcwimberley.com/wp-content/uploads/2026/01/Mike-Stephens-1024x683.jpg'
		}
	];

	const faqs = [
		{
			question: 'Where Do I Park?',
			answer: "Parking at FBC Wimberley is easy. We've got tons of paved parking just out front of our Worship Center."
		},
		{
			question: 'What Is Available For Kids?',
			answer: 'The kids and student ministry at FBC Wimberley is an incredible opportunity for your kids to have fun and learn about Jesus in a safe environment each Sunday! All of our volunteers are trained and background checked. We also offer easy and secure check-in to make drop off a breeze.'
		},
		{
			question: 'What Is A Typical Gathering Like?',
			answer: "Our gatherings are created to provide an environment where you can encounter God whether you've been a believer for decades or have never even heard of Jesus. A typical worship gathering will include three to four songs, a practical teaching time that lasts about thirty minutes, and multiple times of prayer."
		},
		{
			question: 'What Should I Wear?',
			answer: "You'll see everything from suits to T-shirts and shorts. Wear what makes you feel comfortable\u2014you're among family here!"
		},
		{
			question: 'What Times Are Your Sunday Gatherings?',
			answer: 'You can join us each Sunday at 9:30AM and 11:00AM for our worship gatherings. Childcare is provided during both gatherings.'
		},
		{
			question: 'What Do You Believe?',
			answer: 'FBC Wimberley is a Bible-based, Jesus loving church who is committed to the doctrines and theology as laid out in the Baptist Faith and Message of 2000.',
			link: { text: 'Read that document here', href: 'https://bfm.sbc.net/bfm2000/' }
		},
		{
			question: 'How Can I Get More Involved?',
			answer: 'Great question. There are lots of ways to plug in here at FBC Wimberley. The best way is to either visit the "Ministries" or "Groups" section of our website. Or if you\'d like to have a conversation you can email dan@fbcwimberley.com to meet with one of our Pastors.'
		},
		{
			question: 'How Do I Join A Group?',
			answer: 'Groups are the heartbeat of FBC Wimberley because we believe God did not mean for life to be lived alone.',
			link: { text: 'See all of our available groups', href: 'https://fbcwimberley.churchcenter.com/groups' }
		}
	];

	const missionValues = [
		{ word: 'Humbly', desc: 'seek God through prayer and worship.' },
		{ word: 'Boldly', desc: 'teach and preach the truth.' },
		{ word: 'Joyfully', desc: 'love and serve each other, our community and the world.' },
		{ word: 'Faithfully', desc: 'equip disciples.' }
	];

	let openFaq = $state<number | null>(null);
	let expandedStaff = $state<number | null>(null);

	function toggleFaq(i: number) {
		openFaq = openFaq === i ? null : i;
	}

	function toggleStaff(i: number) {
		expandedStaff = expandedStaff === i ? null : i;
	}
</script>

<svelte:head>
	<title>About Us - First Baptist Church Wimberley</title>
</svelte:head>

<!-- Hero -->
<section class="hero">
	<div class="hero-bg" style="background-image: url('https://fbcwimberley.com/wp-content/uploads/2020/02/img-18-1.jpg')"></div>
	<div class="hero-overlay"></div>
	<div class="hero-content">
		<p class="hero-label">Welcome Home</p>
		<h1>Who We Are</h1>
	</div>
</section>

<!-- Our Story -->
<section class="story">
	<div class="story-content container">
		<p class="section-label">Est. 1884</p>
		<h2>Our Story</h2>
		<p class="story-text">
			The history of FBC Wimberley spans back to 1884 when a faithful group of people followed God's call to establish a mission at Jacob's Well. The story of our church, like the story of every person's life, is filled with the marks of God's grace, presence, and calling. Along the way FBC Wimberley has been on mission to be a church FOR our community and our world. FBC Wimberley has had the opportunity to reach our next door neighbors and the nations with the love of Jesus. Join us each Sunday at 9:30AM and 11:00AM to see how God could be writing the next chapter of our story with you!
		</p>
	</div>
</section>

<!-- Vision -->
<section class="vision">
	<div class="vision-bg" style="background-image: url('https://fbcwimberley.com/wp-content/uploads/2025/07/102A5443-scaled.jpg')">
		<div class="vision-overlay"></div>
	</div>
	<div class="vision-content container">
		<p class="section-label">What Drives Us</p>
		<h2>Our Vision</h2>
		<div class="vision-card">
			<p>
				At First Baptist Church of Wimberley we exist to truly know Jesus and to make His Truth known. Our heartbeat is to sincerely experience a relationship with Jesus and help you do the same. We're not interested in knowing a Jesus of cold religion or a Jesus that doesn't challenge our living. Our desire is to experience the Truth of the real Jesus of the Bible and introduce him to the world. We'd love to have you join us.
			</p>
			<blockquote>
				I am the way, and the Truth and the life. No one comes to the Father except through Me.
				<cite>John 14:6</cite>
			</blockquote>
		</div>
	</div>
</section>

<!-- Staff -->
<section class="staff">
	<div class="staff-content container">
		<p class="section-label">Our Team</p>
		<h2>Pastors &amp; Ministry Staff</h2>

		<div class="staff-group-photo">
			<img
				src="https://fbcwimberley.com/wp-content/uploads/2026/01/Staff-1024x683.jpg"
				alt="FBC Wimberley Staff"
				loading="lazy"
			/>
		</div>

		<div class="staff-grid">
			{#each staff as member, i}
				<button class="staff-card" onclick={() => toggleStaff(i)} class:expanded={expandedStaff === i}>
					<div class="staff-image-wrap">
						<img src={member.image} alt={member.name} loading="lazy" />
					</div>
					<h3>{member.name}</h3>
					<p class="staff-title">{member.title}</p>
					{#if member.email}
						<a href="mailto:{member.email}" class="staff-email" onclick={(e) => e.stopPropagation()}>
							<svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"></path><polyline points="22,6 12,13 2,6"></polyline></svg>
							{member.email}
						</a>
					{/if}
					{#if member.bio && expandedStaff === i}
						<p class="staff-bio">{member.bio}</p>
					{/if}
					{#if member.bio}
						<span class="staff-expand">
							{expandedStaff === i ? 'Less' : 'Read more'}
							<svg class:rotated={expandedStaff === i} xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"></polyline></svg>
						</span>
					{/if}
				</button>
			{/each}
		</div>
	</div>
</section>

<!-- Plan Your Visit -->
<section class="visit">
	<div class="visit-bg" style="background-image: url('https://fbcwimberley.com/wp-content/uploads/2025/07/102A6470-scaled.jpg')">
		<div class="visit-overlay"></div>
	</div>
	<div class="visit-content container">
		<p class="section-label">We'd Love To See You</p>
		<h2>Plan Your Visit</h2>
		<div class="visit-card">
			<p>
				Whether you're a young or senior adult, single, or married with kids, you'll feel encouraged by the community we have at FBC Wimberley. You can visit as many times as you want without any obligations or pressure. And who knows&mdash;you just might decide to make FBCW your new church home!
			</p>
		</div>
	</div>
</section>

<!-- FAQs -->
<section class="faqs">
	<div class="faqs-content container">
		<p class="section-label">Got Questions?</p>
		<h2>FAQs</h2>

		<div class="faq-list">
			{#each faqs as faq, i}
				<button class="faq-item" class:open={openFaq === i} onclick={() => toggleFaq(i)}>
					<div class="faq-header">
						<h3>{faq.question}</h3>
						<svg class="faq-chevron" class:rotated={openFaq === i} xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"></polyline></svg>
					</div>
					{#if openFaq === i}
						<div class="faq-answer">
							<p>
								{faq.answer}
								{#if faq.link}
									<a href={faq.link.href} target="_blank" onclick={(e) => e.stopPropagation()}>{faq.link.text}</a>
								{/if}
							</p>
						</div>
					{/if}
				</button>
			{/each}
		</div>
	</div>
</section>

<!-- Mission -->
<section class="mission">
	<div class="mission-bg" style="background-image: url('https://fbcwimberley.com/wp-content/uploads/2022/01/s-h-gue-CjMwAu4-OqY-unsplash-scaled.jpg')">
		<div class="mission-overlay"></div>
	</div>
	<div class="mission-content container">
		<p class="section-label">Our Purpose</p>
		<h2>Our Mission</h2>
		<p class="mission-intro">We are a Christ-centered family, living out the Word of God, as we&hellip;</p>

		<div class="mission-grid">
			{#each missionValues as value}
				<div class="mission-card">
					<h3>{value.word}</h3>
					<p>{value.desc}</p>
				</div>
			{/each}
		</div>
	</div>
</section>

<!-- Contact -->
<section class="contact">
	<div class="contact-content container">
		<p class="section-label">Get In Touch</p>
		<h2>Contact Us</h2>

		<div class="contact-grid">
			<div class="contact-card">
				<div class="contact-icon">
					<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"></path><circle cx="12" cy="10" r="3"></circle></svg>
				</div>
				<h3>Address</h3>
				<p>15951 Winters Mill Parkway<br />Wimberley, Texas 78676</p>
			</div>
			<div class="contact-card">
				<div class="contact-icon">
					<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"></path><polyline points="22,6 12,13 2,6"></polyline></svg>
				</div>
				<h3>Email</h3>
				<p><a href="mailto:office@fbcwimberley.com">office@fbcwimberley.com</a></p>
			</div>
			<div class="contact-card">
				<div class="contact-icon">
					<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"></path></svg>
				</div>
				<h3>Phone</h3>
				<p><a href="tel:5128479035">512-847-9035</a></p>
			</div>
		</div>

		<div class="map-wrap">
			<iframe
				title="First Baptist Church of Wimberley"
				src="https://maps.google.com/maps?q=First%20Baptist%20Church%20of%20Wimberley&t=m&z=10&output=embed&iwloc=near"
				loading="lazy"
				allowfullscreen
			></iframe>
		</div>
	</div>
</section>

<style>
	/* ===== Shared ===== */
	.section-label {
		font-size: 0.8rem;
		font-weight: 600;
		text-transform: uppercase;
		letter-spacing: 0.15em;
		color: var(--color-accent);
		margin-bottom: 0.75rem;
	}

	/* ===== Hero ===== */
	.hero {
		position: relative;
		min-height: 50vh;
		display: flex;
		align-items: flex-end;
		justify-content: center;
		overflow: hidden;
	}

	.hero-bg {
		position: absolute;
		inset: 0;
		background-size: cover;
		background-position: center;
	}

	.hero-overlay {
		position: absolute;
		inset: 0;
		background: linear-gradient(to top, rgba(0,0,0,0.7) 0%, rgba(0,0,0,0.25) 100%);
	}

	.hero-content {
		position: relative;
		z-index: 1;
		text-align: center;
		padding-bottom: 4rem;
	}

	.hero-label {
		font-size: 0.8rem;
		font-weight: 600;
		text-transform: uppercase;
		letter-spacing: 0.15em;
		color: var(--color-accent);
		margin-bottom: 0.75rem;
	}

	.hero h1 {
		font-size: clamp(2.5rem, 6vw, 4rem);
		color: #ffffff;
		text-shadow: 0 2px 20px rgba(0,0,0,0.3);
	}

	/* ===== Story ===== */
	.story {
		padding: 5rem 0;
	}

	.story-content {
		max-width: 800px;
		text-align: center;
	}

	.story-content h2 {
		font-size: clamp(1.75rem, 4vw, 2.5rem);
		margin-bottom: 1.5rem;
	}

	.story-text {
		font-size: 1.05rem;
		line-height: 1.8;
		color: var(--color-text-muted);
	}

	/* ===== Vision ===== */
	.vision {
		position: relative;
		padding: 6rem 0;
		overflow: hidden;
	}

	.vision-bg {
		position: absolute;
		inset: 0;
		background-size: cover;
		background-position: center;
		background-attachment: fixed;
	}

	.vision-overlay {
		position: absolute;
		inset: 0;
		background: linear-gradient(160deg, rgba(26,26,46,0.93) 0%, rgba(26,26,46,0.85) 50%, rgba(44,95,124,0.80) 100%);
	}

	.vision-content {
		position: relative;
		z-index: 1;
		max-width: 800px;
		text-align: center;
	}

	.vision-content h2 {
		font-size: clamp(1.75rem, 4vw, 2.5rem);
		color: #ffffff;
		margin-bottom: 2rem;
	}

	.vision-card {
		background: rgba(255,255,255,0.07);
		backdrop-filter: blur(12px);
		-webkit-backdrop-filter: blur(12px);
		border: 1px solid rgba(255,255,255,0.12);
		border-radius: var(--radius-lg);
		padding: 2.5rem 2rem;
	}

	.vision-card p {
		font-size: 1.05rem;
		color: rgba(255,255,255,0.8);
		line-height: 1.8;
		margin-bottom: 2rem;
	}

	.vision-card blockquote {
		font-family: var(--font-serif);
		font-size: 1.2rem;
		font-style: italic;
		color: #ffffff;
		border-left: 3px solid var(--color-accent);
		padding-left: 1.25rem;
		text-align: left;
	}

	.vision-card blockquote cite {
		display: block;
		margin-top: 0.5rem;
		font-size: 0.85rem;
		font-style: normal;
		color: var(--color-accent);
		font-family: var(--font-sans);
		font-weight: 600;
	}

	/* ===== Staff ===== */
	.staff {
		padding: 5rem 0;
		background: var(--color-bg-alt);
	}

	.staff-content {
		text-align: center;
	}

	.staff-content h2 {
		font-size: clamp(1.75rem, 4vw, 2.5rem);
		margin-bottom: 2.5rem;
	}

	.staff-group-photo {
		border-radius: var(--radius-lg);
		overflow: hidden;
		margin-bottom: 3rem;
	}

	.staff-group-photo img {
		width: 100%;
		height: auto;
		object-fit: cover;
	}

	.staff-grid {
		display: grid;
		grid-template-columns: 1fr;
		gap: 1.25rem;
	}

	.staff-card {
		display: flex;
		flex-direction: column;
		align-items: center;
		text-align: center;
		padding: 1.5rem;
		background: var(--color-bg-card);
		border: 1px solid var(--color-border-light);
		border-radius: var(--radius-lg);
		cursor: pointer;
		transition: all 300ms ease;
		width: 100%;
	}

	.staff-card:hover {
		border-color: var(--color-border);
		box-shadow: var(--shadow-sm);
	}

	.staff-image-wrap {
		width: 120px;
		height: 120px;
		border-radius: var(--radius-full);
		overflow: hidden;
		margin-bottom: 1rem;
		border: 3px solid var(--color-border-light);
	}

	.staff-image-wrap img {
		width: 100%;
		height: 100%;
		object-fit: cover;
	}

	.staff-card h3 {
		font-family: var(--font-sans);
		font-size: 1rem;
		font-weight: 600;
		color: var(--color-heading);
		margin-bottom: 0.25rem;
	}

	.staff-title {
		font-size: 0.85rem;
		color: var(--color-text-muted);
		margin-bottom: 0.5rem;
	}

	.staff-email {
		display: inline-flex;
		align-items: center;
		gap: 0.35rem;
		font-size: 0.8rem;
		color: var(--color-primary);
		transition: color var(--transition);
	}

	.staff-email:hover {
		color: var(--color-primary-hover);
	}

	.staff-bio {
		font-size: 0.9rem;
		color: var(--color-text-muted);
		line-height: 1.7;
		margin-top: 1rem;
		text-align: left;
	}

	.staff-expand {
		display: inline-flex;
		align-items: center;
		gap: 0.25rem;
		margin-top: 0.75rem;
		font-size: 0.8rem;
		font-weight: 600;
		color: var(--color-accent);
	}

	.staff-expand svg {
		transition: transform 200ms ease;
	}

	.staff-expand svg.rotated {
		transform: rotate(180deg);
	}

	/* ===== Plan Your Visit ===== */
	.visit {
		position: relative;
		padding: 6rem 0;
		overflow: hidden;
	}

	.visit-bg {
		position: absolute;
		inset: 0;
		background-size: cover;
		background-position: center;
		background-attachment: fixed;
	}

	.visit-overlay {
		position: absolute;
		inset: 0;
		background: linear-gradient(160deg, rgba(26,26,46,0.93) 0%, rgba(26,26,46,0.85) 50%, rgba(44,95,124,0.80) 100%);
	}

	.visit-content {
		position: relative;
		z-index: 1;
		max-width: 800px;
		text-align: center;
	}

	.visit-content h2 {
		font-size: clamp(1.75rem, 4vw, 2.5rem);
		color: #ffffff;
		margin-bottom: 2rem;
	}

	.visit-card {
		background: rgba(255,255,255,0.07);
		backdrop-filter: blur(12px);
		-webkit-backdrop-filter: blur(12px);
		border: 1px solid rgba(255,255,255,0.12);
		border-radius: var(--radius-lg);
		padding: 2.5rem 2rem;
	}

	.visit-card p {
		font-size: 1.05rem;
		color: rgba(255,255,255,0.8);
		line-height: 1.8;
	}

	/* ===== FAQs ===== */
	.faqs {
		padding: 5rem 0;
	}

	.faqs-content {
		max-width: 800px;
		text-align: center;
	}

	.faqs-content h2 {
		font-size: clamp(1.75rem, 4vw, 2.5rem);
		margin-bottom: 2.5rem;
	}

	.faq-list {
		display: flex;
		flex-direction: column;
		gap: 0.75rem;
		text-align: left;
	}

	.faq-item {
		width: 100%;
		background: var(--color-bg-card);
		border: 1px solid var(--color-border-light);
		border-radius: var(--radius-md);
		padding: 1.25rem 1.5rem;
		cursor: pointer;
		transition: all 300ms ease;
		text-align: left;
	}

	.faq-item:hover {
		border-color: var(--color-border);
	}

	.faq-item.open {
		border-color: var(--color-primary);
		box-shadow: var(--shadow-sm);
	}

	.faq-header {
		display: flex;
		align-items: center;
		justify-content: space-between;
		gap: 1rem;
	}

	.faq-header h3 {
		font-family: var(--font-sans);
		font-size: 0.95rem;
		font-weight: 600;
		color: var(--color-heading);
	}

	.faq-chevron {
		flex-shrink: 0;
		color: var(--color-text-muted);
		transition: transform 200ms ease;
	}

	.faq-chevron.rotated {
		transform: rotate(180deg);
	}

	.faq-answer {
		margin-top: 1rem;
		padding-top: 1rem;
		border-top: 1px solid var(--color-border-light);
	}

	.faq-answer p {
		font-size: 0.95rem;
		color: var(--color-text-muted);
		line-height: 1.7;
	}

	.faq-answer a {
		font-weight: 600;
	}

	/* ===== Mission ===== */
	.mission {
		position: relative;
		padding: 6rem 0;
		overflow: hidden;
	}

	.mission-bg {
		position: absolute;
		inset: 0;
		background-size: cover;
		background-position: center;
		background-attachment: fixed;
	}

	.mission-overlay {
		position: absolute;
		inset: 0;
		background: linear-gradient(160deg, rgba(26,26,46,0.93) 0%, rgba(26,26,46,0.85) 50%, rgba(44,95,124,0.80) 100%);
	}

	.mission-content {
		position: relative;
		z-index: 1;
		max-width: 900px;
		text-align: center;
	}

	.mission-content h2 {
		font-size: clamp(1.75rem, 4vw, 2.5rem);
		color: #ffffff;
		margin-bottom: 1rem;
	}

	.mission-intro {
		font-size: 1.15rem;
		color: rgba(255,255,255,0.8);
		margin-bottom: 2.5rem;
		font-family: var(--font-serif);
		font-style: italic;
	}

	.mission-grid {
		display: grid;
		grid-template-columns: 1fr;
		gap: 1.25rem;
	}

	.mission-card {
		background: rgba(255,255,255,0.07);
		backdrop-filter: blur(12px);
		-webkit-backdrop-filter: blur(12px);
		border: 1px solid rgba(255,255,255,0.12);
		border-radius: var(--radius-lg);
		padding: 2rem 1.5rem;
		transition: all 400ms cubic-bezier(0.23,1,0.32,1);
	}

	.mission-card:hover {
		transform: translateY(-4px);
		background: rgba(255,255,255,0.12);
		border-color: rgba(255,255,255,0.25);
	}

	.mission-card h3 {
		font-size: 1.3rem;
		color: var(--color-accent);
		margin-bottom: 0.5rem;
	}

	.mission-card p {
		font-size: 0.95rem;
		color: rgba(255,255,255,0.7);
		line-height: 1.6;
	}

	/* ===== Contact ===== */
	.contact {
		padding: 5rem 0;
	}

	.contact-content {
		max-width: 900px;
		text-align: center;
	}

	.contact-content h2 {
		font-size: clamp(1.75rem, 4vw, 2.5rem);
		margin-bottom: 2.5rem;
	}

	.contact-grid {
		display: grid;
		grid-template-columns: 1fr;
		gap: 1.25rem;
		margin-bottom: 2.5rem;
	}

	.contact-card {
		background: var(--color-bg-card);
		border: 1px solid var(--color-border-light);
		border-radius: var(--radius-lg);
		padding: 2rem 1.5rem;
		transition: all 300ms ease;
	}

	.contact-card:hover {
		border-color: var(--color-primary);
		box-shadow: var(--shadow-sm);
	}

	.contact-icon {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 52px;
		height: 52px;
		margin: 0 auto 1rem;
		background: var(--color-primary-light);
		color: var(--color-primary);
		border-radius: var(--radius-full);
	}

	.contact-card h3 {
		font-family: var(--font-sans);
		font-size: 0.85rem;
		font-weight: 600;
		text-transform: uppercase;
		letter-spacing: 0.1em;
		color: var(--color-heading);
		margin-bottom: 0.5rem;
	}

	.contact-card p {
		font-size: 0.95rem;
		color: var(--color-text-muted);
		line-height: 1.6;
	}

	.contact-card a {
		color: var(--color-primary);
		font-weight: 500;
	}

	.map-wrap {
		border-radius: var(--radius-lg);
		overflow: hidden;
		border: 1px solid var(--color-border-light);
	}

	.map-wrap iframe {
		width: 100%;
		height: 350px;
		border: 0;
		display: block;
	}

	/* ===== Responsive ===== */
	@media (min-width: 640px) {
		.staff-grid {
			grid-template-columns: repeat(2, 1fr);
		}

		.contact-grid {
			grid-template-columns: repeat(3, 1fr);
		}

		.mission-grid {
			grid-template-columns: repeat(2, 1fr);
		}
	}

	@media (min-width: 768px) {
		.hero {
			min-height: 55vh;
		}

		.vision-card,
		.visit-card {
			padding: 3rem;
		}

		.map-wrap iframe {
			height: 450px;
		}
	}

	@media (min-width: 1024px) {
		.staff-grid {
			grid-template-columns: repeat(3, 1fr);
		}

		.mission-grid {
			grid-template-columns: repeat(4, 1fr);
		}
	}
</style>

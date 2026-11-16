<script lang="ts">
	import ContactBanner from '../../components/contact-banner.svelte';
	import Seo from '../../components/seo.svelte';
	import TopoHeroBg from '../../components/topo-hero-bg.svelte';
	import LinkArrow from '../../components/link-arrow.svelte';
	import PageSpeed from '../../images/open-source/pagespeed.jpg?w=480;800;1200;1600&enhanced';
	import Repositories from '../../images/open-source/repositories.jpg?w=480;800;1200;1600&enhanced';

	const projects = [
		{
			id: 'pagespeed',
			name: 'PageSpeed Score Tracker',
			category: 'Website performance',
			headline: 'Keep an eye on the speed of your sites.',
			description:
				'A single performance test is a snapshot. PageSpeed Score Tracker gives you a place to check your websites and follow their performance over time, so you can see how changes affect the experience.',
			features: [
				'Bring your URLs together in one dashboard.',
				'Review PageSpeed Insights results in a readable view.',
				'Use performance history to spot changes over time.'
			],
			start:
				'Add your sites to the configuration and deploy your own instance. Explore our dashboard to see how we use it for Bootpack Digital.',
			repo: 'pagespeed',
			demo: 'https://pagespeed.bootpack.dev/bootpackdigital',
			demoLabel: 'View our scores',
			image: PageSpeed,
			alt: 'PageSpeed Score Tracker dashboard showing mobile and desktop website scores.',
			caption: 'Mobile and desktop PageSpeed results for Bootpack Digital.',
			code: '',
			codeTitle: ''
		},
		{
			id: 'screenshot-maker',
			name: 'Screenshot Maker',
			category: 'Browser automation',
			headline: 'Turn a URL into a screenshot.',
			description:
				'Capture website previews without opening a browser and cropping each image by hand. Screenshot Maker uses Playwright to generate screenshots through a simple API, useful for visual comparisons, portfolios, and site directories.',
			features: [
				'Set the viewport width and height for the page you want to capture.',
				'Adjust image scale and quality, or capture the full page.',
				'Control access with an API key or allowed referrers.'
			],
			start:
				'Clone the project, copy the environment example, and run it locally or deploy it on Vercel. The README explains the available capture options and access controls.',
			repo: 'screenshot-maker',
			demo: '',
			demoLabel: '',
			image: null,
			alt: '',
			caption: 'Example request: capture a desktop viewport at half size.',
			codeTitle: 'A screenshot from a single request',
			code: 'GET /api/screenshot\n\n?url=https%3A%2F%2Fbootpackdigital.com\n&width=1440\n&height=900\n&scale=0.5\n&quality=80'
		},
		{
			id: 'redirects-wizard',
			name: 'Redirects Wizard',
			category: 'Site migrations',
			headline: 'Give your old links a new home.',
			description:
				'A site migration should not leave visitors at a dead end. Redirects Wizard helps you organize existing URLs, find unresolved pages, and build redirect rules before and after launch.',
			features: [
				'Group production URLs into batches and check their status against a new site.',
				'Assign redirect targets and inspect redirect chains.',
				'Generate rules for Apache, nginx, Caddy, Netlify, Next.js, and Astro.'
			],
			start:
				'Create a batch for your staging or live site, add your old URLs, and map the ones that need a new destination. Export the rules, then recheck your URLs after applying them. A CLI supports scripted workflows, too.',
			repo: 'redirects-wizard',
			demo: 'https://redirectswizard.com',
			demoLabel: 'Visit Redirects Wizard',
			image: null,
			alt: '',
			caption: 'An example migration: map old URLs to their new destinations.',
			codeTitle: 'Old links. Clear destinations.',
			code: '/about-us       →  /about\n/our-work       →  /work\n/get-in-touch   →  /contact\n\nAdd URLs → Check → Map → Export\n\nApache · nginx · Caddy · Netlify\nNext.js · Astro'
		},
		{
			id: 'github-repositories-viewer',
			name: 'GitHub Repositories Viewer',
			category: 'Developer workflow',
			headline: 'See your repositories in one place.',
			description:
				'When work spans multiple repositories, keeping track of access and open pull requests takes time. This viewer brings repositories and contributors into a straightforward overview to help you find what needs attention.',
			features: [
				'Browse your repositories in an easy-to-scan view.',
				'See contributors alongside the projects they work on.',
				'Find open pull requests across your repositories.'
			],
			start:
				'Run your own instance and follow the repository setup instructions to connect it to GitHub. Use the overview to review your projects and the people working on them.',
			repo: 'github-repositories-viewer',
			demo: '',
			demoLabel: '',
			image: Repositories,
			alt: 'GitHub Repositories Viewer showing a list of repositories and their contributors.',
			caption: 'The repository overview, with contributors visible alongside each project.',
			code: '',
			codeTitle: ''
		}
	];
</script>

<Seo
	title="Open-source Projects from Bootpack Digital"
	description="Explore our open-source tools for PageSpeed tracking, website screenshots, redirects, and GitHub workflows. See how they work and get the code."
	canonical="/open-source"
	ogImage="/og-open-source.jpg"
	ogImageAlt="Open-source projects from Bootpack Digital"
/>

<section class="relative overflow-hidden bg-blue-50">
	<TopoHeroBg />
	<div class="relative mx-auto max-w-7xl px-4 py-16 sm:px-6 lg:px-8 lg:py-24">
		<p class="mb-4 text-sm font-semibold tracking-widest text-blue-700 uppercase">
			Built to be shared
		</p>
		<h1 class="max-w-4xl text-4xl font-bold tracking-tight text-navy-700 sm:text-5xl lg:text-6xl">
			Open-source projects.<br />Practical tools for the web.
		</h1>
		<p class="mt-6 max-w-2xl text-lg leading-relaxed text-gray-600">
			Open-source software makes our work possible. These are some of the tools we’re sharing back:
			small, focused projects that help with the everyday work of building and maintaining websites.
		</p>
		<a
			class="mt-7 inline-flex items-center gap-2 font-semibold text-orange-700 underline decoration-orange-300 underline-offset-4 hover:text-orange-800"
			href="https://github.com/michaelbonner?tab=repositories&amp;type=source"
			data-sveltekit-reload>Explore our GitHub projects <LinkArrow /></a
		>
	</div>
</section>

<nav aria-label="Projects on this page" class="border-b border-blue-100 bg-white">
	<div class="mx-auto flex max-w-7xl flex-wrap gap-x-8 gap-y-3 px-4 py-5 sm:px-6 lg:px-8">
		{#each projects as project (project.id)}
			<a
				class="text-sm font-semibold text-navy-700 underline-offset-4 hover:underline"
				href={`#${project.id}`}>{project.name}</a
			>
		{/each}
	</div>
</nav>

<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
	{#each projects as project, index (project.id)}
		<section
			id={project.id}
			aria-labelledby={`${project.id}-title`}
			class="grid scroll-mt-8 items-center gap-10 border-b border-blue-100 py-14 last:border-0 lg:grid-cols-2 lg:gap-16 lg:py-20"
		>
			<div class:lg:order-2={index % 2 !== 0}>
				<p class="mb-3 text-sm font-semibold tracking-wider text-blue-700 uppercase">
					{project.category}
				</p>
				<h2
					id={`${project.id}-title`}
					class="text-3xl font-bold tracking-tight text-navy-700 sm:text-4xl"
				>
					{project.name}
				</h2>
				<p class="mt-4 text-xl font-medium text-navy-600">{project.headline}</p>
				<p class="mt-4 leading-relaxed text-gray-600">{project.description}</p>
				<ul class="mt-6 space-y-3 text-gray-600">
					{#each project.features as feature (feature)}
						<li class="flex gap-3">
							<span aria-hidden="true" class="font-bold text-blue-600">✓</span><span>{feature}</span
							>
						</li>
					{/each}
				</ul>
				<h3 class="mt-7 font-semibold text-navy-700">Get started</h3>
				<p class="mt-2 leading-relaxed text-gray-600">{project.start}</p>
				<div class="mt-7 flex flex-wrap items-center gap-x-6 gap-y-4">
					<a
						class="inline-flex items-center gap-2 rounded-md bg-navy-700 px-5 py-3 font-semibold text-white transition-colors hover:bg-navy-900"
						href={`https://github.com/michaelbonner/${project.repo}`}
						data-sveltekit-reload
						aria-label={`View ${project.name} on GitHub`}>View on GitHub <LinkArrow /></a
					>
					{#if project.demo}<a
							class="inline-flex items-center gap-2 font-semibold text-orange-700 underline-offset-4 hover:underline"
							href={project.demo}
							data-sveltekit-reload>{project.demoLabel} <LinkArrow /></a
						>{/if}
				</div>
			</div>
			<figure class="min-w-0" class:lg:order-1={index % 2 !== 0}>
				{#if project.image}
					<a
						aria-label={`View ${project.name} on GitHub`}
						href={`https://github.com/michaelbonner/${project.repo}`}
						data-sveltekit-reload
						class="block overflow-hidden rounded-xl border border-blue-200 bg-blue-50 p-3 shadow-sm transition-shadow hover:shadow-lg sm:p-5"
					>
						<enhanced:img
							src={project.image}
							alt={project.alt}
							class="h-auto w-full rounded-md border border-gray-200"
							sizes="(min-width: 1024px) 560px, 100vw"
							loading="lazy"
						/>
					</a>
				{:else}
					<div class="overflow-hidden rounded-xl border border-navy-700 bg-navy-900 shadow-sm">
						<div class="flex items-center gap-2 border-b border-white/15 px-5 py-4">
							<span class="size-2.5 rounded-full bg-orange-400"></span><span
								class="size-2.5 rounded-full bg-blue-300"
							></span><span class="size-2.5 rounded-full bg-blue-600"></span><span
								class="ml-3 text-sm text-blue-200">{project.codeTitle}</span
							>
						</div>
						<pre
							class="overflow-x-auto p-5 text-xs leading-loose text-blue-100 sm:p-8 sm:text-sm"><code
								>{project.code}</code
							></pre>
					</div>
				{/if}
				<figcaption class="mt-4 text-sm leading-relaxed text-gray-500">
					{project.caption}
				</figcaption>
			</figure>
		</section>
	{/each}
</div>

<section class="bg-blue-50 px-4 py-14 sm:px-6 lg:px-8">
	<div class="mx-auto max-w-3xl text-center">
		<h2 class="text-2xl font-bold text-navy-700 sm:text-3xl">Found a bug? Have an idea?</h2>
		<p class="mt-4 leading-relaxed text-gray-600">
			Each project has a home on GitHub. Read the setup instructions, open an issue with what you
			found, or share an improvement through a pull request. Check the repository’s license before
			using the code in your own project.
		</p>
	</div>
</section>

<ContactBanner
	textLine1="Ready to build something together?"
	textLine2="Send us a message so we can chat."
	bgColor="bg-navy-100"
/>

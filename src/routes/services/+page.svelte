<script lang="ts">
	import { resolve } from '$app/paths';
	import ContactBanner from '../../components/contact-banner.svelte';
	import LinkArrow from '../../components/link-arrow.svelte';
	import Seo from '../../components/seo.svelte';
	import { services } from '#lib/data/services.js';

	const steps = [
		{
			number: '01',
			title: 'Talk it through',
			body: "We start with a call about what you're trying to build and why. No pitch deck, no discovery fee. You leave that call knowing whether we're the right fit."
		},
		{
			number: '02',
			title: 'Scope and estimate',
			body: 'We write down what gets built, what it costs, and roughly how long it takes. You approve the scope before any code gets written.'
		},
		{
			number: '03',
			title: 'Design and build',
			body: 'You see working software early and often. Short cycles, a staging link you can click through anytime, and a direct line to the person writing the code.'
		},
		{
			number: '04',
			title: 'Launch and support',
			body: "We handle the launch, the monitoring, and whatever comes next. Most clients stay on for ongoing work because the person who built it is still the person fixing it."
		}
	];

	const faqs = [
		{
			question: 'Do you handle both design and development?',
			answer:
				"Yes. Most projects we take on are design and development together, which is usually cheaper and faster than splitting them across two vendors. We're also happy to build from designs your team or another agency produced."
		},
		{
			question: 'Can you build for both iOS and Android?',
			answer:
				'Yes. We build cross platform apps that ship to the App Store and Google Play from a single codebase, so a feature gets designed and built once instead of twice.'
		},
		{
			question: 'Is SEO included, or is it a separate service?',
			answer:
				'The technical foundation is included in every site we build: fast page loads, semantic markup, structured data, clean URLs, and correct metadata. Ongoing SEO work such as audits, content strategy, and reporting is a separate engagement.'
		},
		{
			question: 'What does a project cost?',
			answer:
				'It depends on scope. A marketing site is a very different project from a custom application with user accounts and integrations. We give you a written estimate before work starts, and we bill against an approved scope rather than an open ended hourly meter.'
		},
		{
			question: 'Do you work with clients outside Utah?',
			answer:
				'We do. We are based in Salt Lake City and we love working with local businesses, but most of our clients are remote and spread across the United States.'
		},
		{
			question: 'What happens after launch?',
			answer:
				'We stick around. Hosting, monitoring, security updates, and new features are all things we handle on an ongoing basis. You are never handed a codebase and left to figure it out alone.'
		}
	];

	const servicesJsonLd = {
		'@context': 'https://schema.org',
		'@type': 'CollectionPage',
		name: 'Services',
		description:
			'Design, web development, mobile app development, and SEO services from Bootpack Digital in Salt Lake City, Utah.',
		url: 'https://bootpackdigital.com/services',
		mainEntity: {
			'@type': 'ItemList',
			itemListElement: services.map((service, i) => ({
				'@type': 'ListItem',
				position: i + 1,
				item: {
					'@type': 'Service',
					name: service.title,
					description: service.summary,
					url: `https://bootpackdigital.com/services#${service.id}`,
					areaServed: 'United States',
					provider: { '@id': 'https://bootpackdigital.com/#organization' }
				}
			}))
		}
	};

	const faqJsonLd = {
		'@context': 'https://schema.org',
		'@type': 'FAQPage',
		mainEntity: faqs.map((faq) => ({
			'@type': 'Question',
			name: faq.question,
			acceptedAnswer: {
				'@type': 'Answer',
				text: faq.answer
			}
		}))
	};
</script>

<Seo
	title="Design, Development, and SEO Services | Bootpack Digital"
	description="Design and development for web and mobile applications, plus SEO built into every project. A Salt Lake City studio shipping websites, apps, and custom software."
	canonical="/services"
	jsonLd={[servicesJsonLd, faqJsonLd]}
/>

<section class="px-4 pt-16 pb-14 bg-white sm:px-6 md:pt-24 md:pb-20 lg:px-8">
	<div class="mx-auto max-w-7xl">
		<div class="grid gap-6 items-end md:grid-cols-[1fr_auto] md:gap-12">
			<div>
				<p class="text-sm font-bold tracking-[0.18em] text-orange-700 uppercase">Services</p>
				<h1
					class="mt-4 max-w-3xl text-4xl font-extrabold tracking-tight leading-[1.08] text-navy-700 text-balance sm:text-5xl lg:text-6xl"
				>
					Design, web, mobile, and SEO under one roof
				</h1>
			</div>
			<p class="max-w-md text-lg leading-8 text-navy-600 md:text-right">
				Pick the one you need or combine them. Here's exactly what each one covers.
			</p>
		</div>

		<nav aria-label="Services" class="mt-12 md:mt-16">
			<ol class="grid border-t border-blue-200 sm:grid-cols-2 lg:grid-cols-4">
				{#each services as service, i (service.id)}
					<li
						class="border-b border-blue-200 sm:odd:border-r lg:border-b-0 lg:border-r lg:last:border-r-0"
					>
						<a
							class="group flex flex-col h-full py-6 transition-colors sm:px-6 hover:bg-blue-50 focus-visible:outline-2 focus-visible:-outline-offset-2 focus-visible:outline-navy-600 lg:py-8"
							href="#{service.id}"
						>
							<div class="flex justify-between items-center">
								<span class="text-sm font-bold tracking-[0.16em] text-orange-700 tabular-nums">
									{String(i + 1).padStart(2, '0')}
								</span>
								<svg
									aria-hidden="true"
									class="size-6 text-blue-600"
									fill="none"
									stroke="currentColor"
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="1.5"
									viewBox="0 0 24 24"
									xmlns="http://www.w3.org/2000/svg"
								><path d={service.path}></path></svg>
							</div>
							<span class="mt-5 text-xl font-bold tracking-tight text-navy-700">
								{service.shortTitle}
							</span>
							<span class="mt-2 text-base leading-7 text-gray-600">{service.shortSummary}</span>
							<span
								class="inline-flex items-center pt-5 mt-auto text-sm font-semibold text-blue-700 group-hover:text-blue-500"
							>
								What's included
								<LinkArrow class="ml-1.5 rotate-90 transition-transform group-hover:translate-y-0.5" />
							</span>
						</a>
					</li>
				{/each}
			</ol>
		</nav>
	</div>
</section>

{#each services as service, i (service.id)}
	<section
		class={[
			'px-4 py-16 scroll-mt-16 sm:px-6 md:py-24 lg:px-8',
			i % 2 === 0 ? 'bg-blue-50' : 'bg-white'
		]}
		aria-labelledby="{service.id}-title"
		id={service.id}
	>
		<div
			class="grid gap-10 mx-auto max-w-7xl lg:grid-cols-[minmax(0,5fr)_minmax(0,7fr)] lg:gap-20"
		>
			<div class="lg:sticky lg:top-28 lg:self-start">
				<p
					aria-hidden="true"
					class="text-7xl font-extrabold tracking-tight leading-none text-blue-200 tabular-nums sm:text-8xl"
				>
					{String(i + 1).padStart(2, '0')}
				</p>
				<div class="flex gap-3 items-center mt-6">
					<svg
						aria-hidden="true"
						class="size-6 text-blue-600"
						fill="none"
						stroke="currentColor"
						stroke-linecap="round"
						stroke-linejoin="round"
						stroke-width="1.5"
						viewBox="0 0 24 24"
						xmlns="http://www.w3.org/2000/svg"
					><path d={service.path}></path></svg>
					<p class="text-sm font-bold tracking-[0.16em] text-orange-700 uppercase">
						{service.eyebrow}
					</p>
				</div>
				<h2
					class="mt-3 text-3xl font-bold tracking-tight text-navy-700 text-balance sm:text-4xl"
					id="{service.id}-title"
				>
					{service.title}
				</h2>

				<ul aria-label="Tools and focus areas" class="flex flex-wrap gap-2 mt-6">
					{#each service.tags as tag (tag)}
						<li
							class="py-1.5 px-3 text-sm font-semibold bg-white rounded-full border border-blue-200 text-navy-600"
						>
							{tag}
						</li>
					{/each}
				</ul>
			</div>

			<div>
				<p class="text-xl leading-9 text-navy-600">{service.summary}</p>

				<h3 class="mt-10 text-xs font-bold tracking-[0.16em] text-navy-600 uppercase">
					What you get
				</h3>

				<ul class="mt-4 border-t border-blue-200">
					{#each service.deliverables as deliverable (deliverable)}
						<li
							class="flex gap-4 items-start py-4 text-lg leading-7 border-b border-blue-200 text-navy-700"
						>
							<svg
								aria-hidden="true"
								class="mt-1 text-blue-600 size-5 shrink-0"
								fill="none"
								stroke="currentColor"
								stroke-linecap="round"
								stroke-linejoin="round"
								stroke-width="2.5"
								viewBox="0 0 24 24"
								xmlns="http://www.w3.org/2000/svg"
							><path d="M5 13l4 4L19 7"></path></svg>

							{deliverable}
						</li>
					{/each}
				</ul>

				<a
					class="inline-flex items-center mt-8 font-semibold text-blue-700 underline decoration-blue-300 underline-offset-4 hover:text-blue-500 focus-visible:outline-2 focus-visible:outline-offset-4 focus-visible:outline-navy-600"
					href={resolve('contact')}
				>
					Get a quote for this<span class="sr-only"> service: {service.title}</span>
					<LinkArrow class="ml-2" />
				</a>
			</div>
		</div>
	</section>
{/each}

<section class="px-4 py-16 bg-navy-800 sm:px-6 md:py-24 lg:px-8 lg:py-28">
	<div class="mx-auto max-w-7xl">
		<div class="grid gap-6 items-end mb-12 md:grid-cols-[1fr_auto] md:mb-16">
			<div>
				<p class="text-sm font-bold tracking-[0.16em] text-orange-300 uppercase">How it goes</p>
				<h2 class="mt-3 text-3xl font-bold tracking-tight text-white sm:text-4xl">
					What working with us looks like
				</h2>
			</div>
			<p class="max-w-md text-base leading-7 text-navy-100 md:text-right">
				No account managers, no handoffs to a team you've never met. You work directly with the
				people building your project.
			</p>
		</div>

		<ol class="grid gap-6 md:grid-cols-2 lg:grid-cols-4 lg:gap-8">
			{#each steps as step (step.number)}
				<li class="p-7 rounded-2xl border bg-navy-900/40 border-navy-600">
					<p class="text-3xl font-extrabold tracking-tight text-blue-300">{step.number}</p>
					<h3 class="mt-4 text-xl font-bold tracking-tight text-white">{step.title}</h3>
					<p class="mt-3 text-base leading-7 text-navy-100">{step.body}</p>
				</li>
			{/each}
		</ol>

		<a
			class="inline-flex items-center mt-12 font-semibold text-white underline decoration-blue-300 underline-offset-4 hover:text-blue-200 focus-visible:outline-2 focus-visible:outline-offset-4 focus-visible:outline-blue-300"
			href={resolve('blog/how-we-work-with-you')}
		>
			Read more about how we run projects
			<LinkArrow class="ml-2" />
		</a>
	</div>
</section>

<section class="px-4 py-16 bg-white sm:px-6 md:py-24 lg:px-8 lg:py-28">
	<div class="mx-auto max-w-7xl">
		<div class="grid gap-8 items-start lg:grid-cols-[minmax(0,0.9fr)_minmax(0,1.1fr)] lg:gap-20">
			<div>
				<p class="text-sm font-bold tracking-[0.16em] text-orange-700 uppercase">Questions</p>
				<h2 class="mt-3 text-3xl font-bold tracking-tight text-navy-700 sm:text-4xl">
					The things clients ask first
				</h2>
				<p class="mt-5 text-base leading-7 text-gray-600">
					Still not sure where your project fits? Send us a note and we'll tell you straight whether
					we're the right team for it.
				</p>
				<a
					class="inline-flex items-center mt-6 font-semibold text-blue-700 underline decoration-blue-300 underline-offset-4 hover:text-blue-500 focus-visible:outline-2 focus-visible:outline-offset-4 focus-visible:outline-navy-600"
					href={resolve('contact')}
				>Ask us anything <LinkArrow class="ml-2" /></a>
			</div>

			<dl class="grid gap-8">
				{#each faqs as faq (faq.question)}
					<div class="pb-8 border-b border-blue-200 last:pb-0 last:border-b-0">
						<dt class="text-xl font-bold tracking-tight text-navy-700">{faq.question}</dt>
						<dd class="mt-3 text-base leading-7 text-gray-600">{faq.answer}</dd>
					</div>
				{/each}
			</dl>
		</div>
	</div>
</section>

<ContactBanner
	textLine1="Know what you need built?"
	textLine2="Let's talk through the scope."
	bgColor="bg-navy-100"
/>

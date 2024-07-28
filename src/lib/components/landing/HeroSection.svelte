<script lang="ts">
	import { ArrowRightIcon } from 'lucide-svelte';
	import AnimatedShinyText from '$lib/components/magic/AnimatedShinyText/AnimatedShinyText.svelte';
	import BorderBeam from '$lib/components/magic/borderbeam/BorderBeam.svelte';
	import Button from '$lib/components/ui/button/button.svelte';
	import type { ObserverEventDetails } from 'svelte-inview';
	import { inview } from 'svelte-inview';

	// Images
	import HeroDarkImg from '$lib/imgs/hero-dark.png';
	import HeroLightImg from '$lib/imgs/hero-light.png';
	let inView = false;
	const handleChange = ({ detail }: CustomEvent<ObserverEventDetails>) => {
		// console.log(detail);
		inView = detail.inView;
	};
</script>

<section id="hero" class="relative mx-auto mt-32 max-w-7xl px-6 text-center md:px-8">
	<div
		class="backdrop-filter-[12px] group inline-flex h-7 -translate-y-4 animate-fade-in items-center justify-between gap-1 rounded-full border border-white/5 bg-white/10 px-3 text-xs text-white opacity-0 transition-all ease-in hover:cursor-pointer hover:bg-white/20 dark:text-black"
	>
		<AnimatedShinyText class="inline-flex items-center justify-center">
			<span>✨ Introducing Svee UI Template</span>
			{' '}
			<ArrowRightIcon
				class="ml-1 size-3 transition-transform duration-300 ease-in-out group-hover:translate-x-0.5"
			/>
		</AnimatedShinyText>
	</div>
	<h1
		class="-translate-y-4 animate-fade-in text-balance bg-gradient-to-br from-black from-30% to-black/40 bg-clip-text py-6 text-5xl font-medium leading-none tracking-tighter text-transparent opacity-0 [--animation-delay:200ms] dark:from-white dark:to-white/40 sm:text-6xl md:text-7xl lg:text-8xl"
	>
		Svee UI is the new way
		<br class="hidden md:block" />
		{' '}
		to build landing pages.
	</h1>
	<p
		class="mb-12 -translate-y-4 animate-fade-in text-balance text-lg tracking-tight text-gray-400 opacity-0 [--animation-delay:400ms] md:text-xl"
	>
		Beautifully designed, animated components and templates built with
		<br class="hidden md:block" />
		{' '}
		Tailwind CSS, <a href="https://svelte.dev" class="underline underline-offset-2">Svelte</a>, and
		<a href="https://animation-svelte.vercel.app" class="underline underline-offset-2">Svelte Animations</a>.
	</p>
	<Button
		class="-translate-y-4 animate-fade-in gap-1 rounded-lg text-white opacity-0 ease-in-out [--animation-delay:600ms] dark:text-black"
	>
		<span>Get Started for free </span>
		<ArrowRightIcon
			class="ml-1 size-4 transition-transform duration-300 ease-in-out group-hover:translate-x-1"
		/>
	</Button>
	<div
		use:inview={{
			unobserveOnEnter: true,
			rootMargin: '-100px'
		}}
		on:inview_change={handleChange}
		class="relative mt-32 animate-fade-up opacity-0 [--animation-delay:400ms] [perspective:2000px] after:absolute after:inset-0 after:z-50 after:[background:linear-gradient(to_top,hsl(var(--background))_30%,transparent)]"
	>
		<div
			class="rounded-xl border border-white/10 bg-white bg-opacity-[0.01] before:absolute before:bottom-1/2 before:left-0 before:top-0 before:size-full before:opacity-0 before:[background-image:linear-gradient(to_bottom,var(--color-one),var(--color-one),transparent_40%)] before:[filter:blur(180px)] {inView
				? 'before:animate-image-glow'
				: ''}"
		>
			<BorderBeam
				size={200}
				duration={12}
				delay={0}
				colorFrom="var(--color-one)"
				colorTo="var(--color-two)"
			/>

			<img
				src={HeroDarkImg}
				alt="HeroDarkImage"
				class="relative hidden size-full rounded-[inherit] border object-contain dark:block"
			/>
			<img
				src={HeroLightImg}
				alt="HeroLightImage"
				class="relative block size-full rounded-[inherit] border object-contain dark:hidden"
			/>
		</div>
	</div>
</section>

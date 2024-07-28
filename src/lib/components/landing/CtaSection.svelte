<script lang="ts">
	import { BarChart, ChevronRight, File, Globe, HeartHandshake, Rss, Shield } from 'lucide-svelte';
	import Marquee from '../magic/marquee/Marquee.svelte';
	import CtaCard from './CtaCard.svelte';
	import Button from '../ui/button/button.svelte';
	let tiles: { icon: any; bg: string }[] = [
		{
			icon: HeartHandshake,
			bg: 'pointer-events-none absolute left-1/2 top-1/2 size-1/2 -translate-x-1/2 -translate-y-1/2 overflow-visible rounded-full bg-gradient-to-r from-orange-600 via-rose-600 to-violet-600 opacity-70 blur-[20px]'
		},
		{
			icon: Globe,
			bg: 'pointer-events-none absolute left-1/2 top-1/2 size-1/2 -translate-x-1/2 -translate-y-1/2 overflow-visible rounded-full bg-gradient-to-r from-cyan-500 via-blue-500 to-indigo-500 opacity-70 blur-[20px]'
		},
		{
			icon: File,
			bg: 'pointer-events-none absolute left-1/2 top-1/2 size-1/2 -translate-x-1/2 -translate-y-1/2 overflow-visible rounded-full bg-gradient-to-r from-green-500 via-teal-500 to-emerald-600 opacity-70 blur-[20px]'
		},
		{
			icon: Shield,
			bg: 'pointer-events-none absolute left-1/2 top-1/2 size-1/2 -translate-x-1/2 -translate-y-1/2 overflow-visible rounded-full bg-gradient-to-r from-yellow-400 via-orange-500 to-yellow-600 opacity-70 blur-[20px]'
		},
		{
			icon: Rss,
			bg: 'pointer-events-none absolute left-1/2 top-1/2 size-1/2 -translate-x-1/2 -translate-y-1/2 overflow-visible rounded-full bg-gradient-to-r from-orange-600 via-rose-600 to-violet-600 opacity-70 blur-[20px]'
		},
		{
			icon: BarChart,
			bg: 'pointer-events-none absolute left-1/2 top-1/2 size-1/2 -translate-x-1/2 -translate-y-1/2 overflow-visible rounded-full bg-gradient-to-r from-gray-600 via-gray-500 to-gray-400 opacity-70 blur-[20px]'
		}
	];
	function shuffleArray(array: any[]) {
		let currentIndex = array.length;
		let randomIndex;
		// While there remain elements to shuffle.
		while (currentIndex !== 0) {
			// Pick a remaining element.
			randomIndex = Math.floor(Math.random() * currentIndex);
			currentIndex--;
			// And swap it with the current element.
			[array[currentIndex], array[randomIndex]] = [array[randomIndex], array[currentIndex]];
		}
		return array;
	}
	let randomTiles1 = shuffleArray(tiles);
	let randomTiles2 = shuffleArray(tiles);
	let randomTiles3 = shuffleArray(tiles);
	let randomTiles4 = shuffleArray(tiles);
</script>

<section id="cta">
	<div class="py-14">
		<div class="flex w-full flex-col items-center justify-center">
			<div class="relative flex w-full flex-col items-center justify-center overflow-hidden">
				<Marquee reverse class="-delay-[200ms] [--duration:10s]" repeat={5}>
					{#each randomTiles1 as { icon, bg }, id}
						<CtaCard>
							<svelte:component this={icon} class="size-full" />
							<div class={bg}></div>
						</CtaCard>
					{/each}
				</Marquee>
				<Marquee reverse class="[--duration:25s]" repeat={5}>
					{#each randomTiles2 as { icon, bg }, id}
						<CtaCard>
							<svelte:component this={icon} class="size-full" />
							<div class={bg}></div>
						</CtaCard>
					{/each}
				</Marquee>
				<Marquee reverse class="-delay-[200ms] [--duration:20s]" repeat={5}>
					{#each randomTiles1 as { icon, bg }, id}
						<CtaCard>
							<svelte:component this={icon} class="size-full" />
							<div class={bg}></div>
						</CtaCard>
					{/each}
				</Marquee>
				<Marquee reverse class="[--duration:30s]" repeat={5}>
					{#each randomTiles2 as { icon, bg }, id}
						<CtaCard>
							<svelte:component this={icon} class="size-full" />
							<div class={bg}></div>
						</CtaCard>
					{/each}
				</Marquee>
				<Marquee reverse class="-delay-[200ms] [--duration:20s]" repeat={5}>
					{#each randomTiles3 as { icon, bg }, id}
						<CtaCard>
							<svelte:component this={icon} class="size-full" />
							<div class={bg}></div>
						</CtaCard>
					{/each}
				</Marquee>
				<Marquee reverse class="[--duration:30s]" repeat={5}>
					{#each randomTiles4 as { icon, bg }, id}
						<CtaCard>
							<svelte:component this={icon} class="size-full" />
							<div class={bg}></div>
						</CtaCard>
					{/each}
				</Marquee>
				<div class="absolute z-10">
					<div
						class="mx-auto size-24 rounded-[2rem] border bg-white/10 p-3 shadow-2xl backdrop-blur-md dark:bg-black/10 lg:size-32"
					>
						<HeartHandshake class="mx-auto size-16 text-black dark:text-white lg:size-24" />
					</div>
					<div class="z-10 mt-4 flex flex-col items-center text-center text-primary">
						<h1 class="text-3xl font-bold lg:text-4xl">Stop wasting time on design.</h1>
						<p class="mt-2">Start your 7-day free trial. No credit card required.</p>
						<Button size="lg" variant="outline" href="#" class="group mt-4 rounded-[2rem] px-6">
							Get Started
							<ChevronRight
								class="ml-1 size-4 transition-all duration-300 ease-out group-hover:translate-x-1"
							/>
						</Button>
					</div>
					<div
						class="bg-backtround absolute inset-0 -z-10 rounded-full opacity-40 blur-xl dark:bg-background"
					/>
				</div>
				<div
					class="to-backtround absolute inset-x-0 bottom-0 h-full bg-gradient-to-b from-transparent to-70% dark:to-background"
				/>
			</div>
		</div>
	</div>
</section>

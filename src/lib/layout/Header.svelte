<script>
	import Button from '$lib/components/ui/button/button.svelte';
	import { cn } from '$lib/utils';
	import { AlignJustify, XIcon } from 'lucide-svelte';
	import { AnimatePresence, Motion } from 'svelte-motion';

	const menuItem = [
		{
			id: 1,
			label: 'Features',
			href: '#'
		},
		{
			id: 2,
			label: 'Pricing',
			href: '#'
		},
		{
			id: 3,
			label: 'Careers',
			href: '#'
		},
		{
			id: 4,
			label: 'Contact Us',
			href: '#'
		}
	];
	const mobilenavbarVariant = {
		initial: {
			opacity: 0,
			scale: 1
		},
		animate: {
			scale: 1,
			opacity: 1,
			transition: {
				duration: 0.2,
				ease: 'easeOut'
			}
		},
		exit: {
			opacity: 0,
			transition: {
				duration: 0.2,
				delay: 0.2,
				ease: 'easeOut'
			}
		}
	};

	const mobileLinkVar = {
		initial: {
			y: '-20px',
			opacity: 0
		},
		open: {
			y: 0,
			opacity: 1,
			transition: {
				duration: 0.3,
				ease: 'easeOut'
			}
		}
	};

	const containerVariants = {
		open: {
			transition: {
				staggerChildren: 0.06
			}
		}
	};
	import { onMount, onDestroy } from 'svelte';
	import { writable } from 'svelte/store';

	let hamburgerMenuIsOpen = writable(false);

	function toggleOverflowHidden(isOpen) {
		const html = document.querySelector('html');
		if (html) {
			if (isOpen) {
				html.classList.add('overflow-hidden');
			} else {
				html.classList.remove('overflow-hidden');
			}
		}
	}

	$: $hamburgerMenuIsOpen;
	onMount(() => {
		toggleOverflowHidden($hamburgerMenuIsOpen);
		return () => {
			toggleOverflowHidden(false);
		};
	});

	function closeHamburgerNavigation() {
		hamburgerMenuIsOpen.set(false);
	}

	onMount(() => {
		window.addEventListener('orientationchange', closeHamburgerNavigation);
		window.addEventListener('resize', closeHamburgerNavigation);

		return () => {
			window.removeEventListener('orientationchange', closeHamburgerNavigation);
			window.removeEventListener('resize', closeHamburgerNavigation);
		};
	});
</script>

<header
	class="fixed left-0 top-0 z-50 w-full -translate-y-4 animate-fade-in border-b opacity-0 backdrop-blur-md [--animation-delay:600ms]"
>
	<div class="container flex h-14 items-center justify-between">
		<a class="text-md flex items-center" href="/"> Nyxb UI </a>

		<div class="ml-auto flex h-full items-center">
			<a class="mr-6 text-sm" href="/signin"> Log in </a>
			<Button variant="secondary" class="mr-6 text-sm" href="/signup">Sign up</Button>
		</div>
		<button class="ml-6 md:hidden" on:click={() => ($hamburgerMenuIsOpen = !$hamburgerMenuIsOpen)}>
			<span class="sr-only">Toggle menu</span>
			{#if $hamburgerMenuIsOpen}
				<XIcon />
			{:else}
				<AlignJustify />
			{/if}
		</button>
	</div>
</header>
<AnimatePresence let:item list={[{ key: 'a' }]}>
	<Motion
		initial="initial"
		exit="exit"
		variants={mobilenavbarVariant}
		animate={$hamburgerMenuIsOpen ? 'animate' : 'exit'}
		let:motion
	>
		<nav
			use:motion
			class={cn(
				`fixed left-0 top-0 z-50 h-screen w-full overflow-auto bg-background/70 backdrop-blur-md `,
				{
					'pointer-events-none': !$hamburgerMenuIsOpen
				}
			)}
		>
			<div class="container flex h-14 items-center justify-between">
				<a class="text-md flex items-center" href="/"> Nyxb UI </a>

				<button class="md:hidden" on:click={() => ($hamburgerMenuIsOpen = !$hamburgerMenuIsOpen)}>
					<span class="sr-only">Toggle menu</span>
					{#if $hamburgerMenuIsOpen}
						<XIcon strokeWidth={1.6} />
					{:else}
						<AlignJustify strokeWidth={1.6} />
					{/if}
				</button>
			</div>
			<Motion
				variants={containerVariants}
				initial="initial"
				animate={$hamburgerMenuIsOpen ? 'open' : 'exit'}
				let:motion
			>
				<ul
					use:motion
					class="flex flex-col uppercase ease-in md:flex-row md:items-center md:normal-case"
				>
					{#each menuItem as item}
						<Motion variants={mobileLinkVar} let:motion>
							<li use:motion class="border-grey-dark border-b py-0.5 pl-6 md:border-none">
								<a
									class="hover:text-grey flex h-[var(--navigation-height)] w-full items-center text-xl transition-[color,transform] duration-300 md:translate-y-0 md:text-sm md:transition-colors {$hamburgerMenuIsOpen
										? '[&_a]:translate-y-0'
										: ''}"
									href={item.href}
								>
									{item.label}
								</a>
							</li>
						</Motion>
					{/each}
				</ul>
			</Motion>
		</nav>
	</Motion>
</AnimatePresence>

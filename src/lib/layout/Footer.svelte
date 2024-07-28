<script>
	import DiscordSvg from '$lib/imgs/discord.svg';
	import TwitterSvg from '$lib/imgs/x.svg';

	const footerNavs = [
		{
			label: 'Product',
			items: [
				{
					href: '/',
					name: 'Email Collection'
				},
				{
					href: '/pricing',
					name: 'Pricing'
				},
				{
					href: '/faq',
					name: 'FAQ'
				}
			]
		},

		{
			label: 'Community',
			items: [
				{
					href: '/',
					name: 'Discord'
				},
				{
					href: '/',
					name: 'Twitter'
				},
				{
					href: 'mailto:hello@chatcollect.com',
					name: 'Email'
				}
			]
		},
		{
			label: 'Legal',
			items: [
				{
					href: '/terms',
					name: 'Terms'
				},

				{
					href: '/privacy',
					name: 'Privacy'
				}
			]
		}
	];

	const footerSocials = [
		{
			href: '',
			name: 'Discord',
			icon: DiscordSvg
		},
		{
			href: '',
			name: 'Twitter',
			icon: TwitterSvg
		}
	];
</script>

<footer>
	<div class="mx-auto w-full max-w-screen-xl xl:pb-2">
		<div class="gap-4 p-4 px-8 py-16 sm:pb-16 md:flex md:justify-between">
			<div class="mb-12 flex flex-col gap-4">
				<a href="https://animation-svelte.vercel.app" class="flex items-center gap-2">
					<svg
						xmlns="http://www.w3.org/2000/svg"
						width="24"
						height="24"
						viewBox="0 0 24 24"
						fill="none"
						stroke="currentColor"
						stroke-width="1"
						stroke-linecap="round"
						stroke-linejoin="round"
						class="lucide lucide-floor-plan size-8"
						><path
							d="M9 21H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2h-5"
						/><path d="M9 3v7" /><path d="M21 10h-7" /><path d="M3 15h9" /></svg
					>
					<span class="self-center whitespace-nowrap text-2xl font-semibold dark:text-white">
						Svee UI
					</span>
				</a>
				<p class="max-w-xs">UI Library for Design Engineers</p>
			</div>
			<div class="grid grid-cols-1 gap-8 sm:grid-cols-3 sm:gap-10">
				{#each footerNavs as nav}
					<div>
						<h2
							class="mb-6 text-sm font-medium uppercase tracking-tighter text-gray-900 dark:text-white"
						>
							{nav.label}
						</h2>
						<ul class="grid gap-2">
							{#each nav.items as item}
								<li>
									<a
										href={item.href}
										class="cursor-pointer text-sm font-[450] text-gray-400 duration-200 hover:text-gray-200"
									>
										{item.name}
									</a>
								</li>
							{/each}
						</ul>
					</div>
				{/each}
			</div>
		</div>

		<div
			class="flex flex-col gap-2 rounded-md border-neutral-700/20 px-8 py-4 sm:flex sm:flex-row sm:items-center sm:justify-between"
		>
			<div class="flex items-center space-x-5 sm:mt-0 sm:justify-center">
				{#each footerSocials as social}
					<a
						href={social.href}
						class="fill-gray-500 text-gray-500 hover:fill-gray-900 hover:text-gray-900 dark:hover:fill-gray-600 dark:hover:text-gray-600"
					>
						<img src={social.icon} class="size-4" alt={social.name} />
						<span class="sr-only">{social.name}</span>
					</a>
				{/each}
			</div>
			<span class="text-sm text-gray-500 dark:text-gray-400 sm:text-center">
				Copyright ©
				{' '}
				{new Date().getFullYear()}
				{' '}
				<a href="/" class="cursor-pointer">Svee UI</a>
				. All Rights Reserved.
			</span>
		</div>
	</div>
	<!-- Site Banner -->
</footer>

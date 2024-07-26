<script>
	import GoogleSvg from '$lib/imgs/Google.svg';
	import GitHubSvg from '$lib/imgs/GitHub.svg';
	import UberSvg from '$lib/imgs/Uber.svg';
	import MicrosoftSvg from '$lib/imgs/Microsoft.svg';
	import NotionSvg from '$lib/imgs/Notion.svg';
</script>

<section id="clients" class="mx-auto max-w-7xl px-6 text-center md:px-8">
	<div class="py-14">
		<div class="mx-auto max-w-screen-xl px-4 md:px-8">
			<h2 class="text-center text-sm font-semibold text-gray-600">
				TRUSTED BY TEAMS FROM AROUND THE WORLD
			</h2>
			<div class="mt-6">
				<ul
					class="flex flex-wrap items-center justify-center gap-x-10 gap-y-6 md:gap-x-16 [&_path]:fill-white"
				>
					<li>
						<img
							alt="Google"
							src={GoogleSvg}
							class="h-8 w-28 px-2 dark:brightness-0 dark:invert"
							width={28}
							height={8}
						/>
					</li>
					<li>
						<img
							alt="Microsoft"
							src={MicrosoftSvg}
							class="h-8 w-28 px-2 dark:brightness-0 dark:invert"
							width={28}
							height={8}
						/>
					</li>
					<li>
						<img
							alt="GitHub"
							src={GitHubSvg}
							class="h-8 w-28 px-2 dark:brightness-0 dark:invert"
							width={28}
							height={8}
						/>
					</li>

					<li>
						<img
							alt="Uber"
							src={UberSvg}
							class="h-8 w-28 px-2 dark:brightness-0 dark:invert"
							width={28}
							height={8}
						/>
					</li>
					<li>
						<img
							alt="Notion"
							src={NotionSvg}
							class="h-8 w-28 px-2 dark:brightness-0 dark:invert"
							width={28}
							height={8}
						/>
					</li>
				</ul>
			</div>
		</div>
	</div>
</section>

<script lang="ts">
	import { cn } from '$lib/utils';
	export let reverse: boolean = false;
</script>

<div
	class={cn(
		// color
		'[--color:var(--color-one)]',
		'pointer-events-none relative  mx-auto h-[50rem] overflow-hidden',

		// sphere mask
		'[mask-image:radial-gradient(ellipse_at_center_center,#000,transparent_50%)]',

		// reverse
		reverse ? 'my-[-22rem] rotate-180 md:mt-[-30rem]' : 'my-[-18.8rem]',

		// before
		'before:absolute before:inset-0 before:size-full before:opacity-40 before:[background-image:radial-gradient(circle_at_bottom_center,var(--color),transparent_70%)]',

		// after
		'after:absolute after:-left-1/2 after:top-1/2 after:aspect-[1/0.7] after:w-[200%] after:rounded-[50%] after:border-t after:border-[hsl(var(--border))] after:bg-background'
	)}
></div>

<script lang="ts">
	import { onMount } from 'svelte';

	export let row = 0;
	export let col = 0;
	export let width = 1;
	export let height = 1;
	export let cw = 0;
	export let rh = 0;

	let time = new Date();

	onMount(() => {
		const interval = setInterval(() => (time = new Date()), 100); // 100ms are way more accurate than 1s

		return () => clearInterval(interval);
	});

	$: widthOriented = width * cw < height * rh;
</script>

<div
	class="absolute flex flex-col items-center justify-center gap-4 overflow-hidden p-4"
	style="top: {row * rh}px; left: {col * cw}px; width: {width * cw}px; height: {height * rh}px;"
>
	<div
		style="font-size: {widthOriented
			? (width * cw) / 5
			: (height * rh) / 5}px; line-height: {widthOriented
			? (width * cw) / 5
			: (height * rh) / 5}px;"
	>
		{time.toLocaleTimeString(undefined, {
			hour: '2-digit',
			minute: '2-digit',
			second: '2-digit',
			hour12: false
		})}
	</div>
	<div
		style="font-size: {widthOriented
			? (width * cw) / 10
			: (height * rh) / 10}px; line-height: {widthOriented
			? (width * cw) / 10
			: (height * rh) / 10}px;"
	>
		{time.toLocaleDateString('de-DE', {
			year: 'numeric',
			month: '2-digit',
			day: '2-digit'
		})}
	</div>
</div>

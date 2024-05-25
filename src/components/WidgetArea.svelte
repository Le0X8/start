<script lang="ts">
	import TimeWidget from '$c/widgets/Time.svelte';
	type WidgetConstructor = {
		type: string;
		col: number;
		row: number;
    width: number;
    height: number;
	};

	export let widgets: WidgetConstructor[];
  export let cols: number;
  export let rows: number;

  let innerWidth = 0;
  let innerHeight = 0;

  $: colWidth = innerWidth / cols;
  $: rowHeight = innerHeight / rows;
</script>

<svelte:window bind:innerWidth bind:innerHeight />

<div class="h-lvh w-lvw bg-black text-white">
	{#each widgets as widget}
    {#if widget.type === 'time'}
      <TimeWidget col={widget.col - 1} row={widget.row - 1} width={widget.width} height={widget.height} cw={colWidth} rh={rowHeight} />
    {/if}
	{/each}
</div>

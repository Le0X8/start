<script lang="ts">
	import WidgetArea from '$c/WidgetArea.svelte';

  const widgets = [
    {type: 'time', col: 1, row: 1, width: 16, height: 9},
  ];
</script>

<main>
	<WidgetArea {widgets} cols={16} rows={9} />
</main>

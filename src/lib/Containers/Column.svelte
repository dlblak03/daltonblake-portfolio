<script lang="ts">
	export let includeHover = false;
	export let dark = false;

	export let alignitems = 'flex-start';
	export let justifycontent = 'flex-start';
	export let gap = '0';
	export let grow = '1';
	export let wrap = 'nowrap';

	export let minheight = 'none';
	export let maxheight = 'none';
	export let minwidth = 'none';
	export let maxwidth = 'none';

	export let padding = '0 0 0 0';
	export let margin = '0 0 0 0';

	export let background = 'white';
	export let border = 'none';
	export let borderright = 'default';
	export let borderleft = 'default';
	export let borderbottom = 'default';
	export let bordertop = 'default';
	export let borderradius = '0';
	export let boxshadow = 'none';
	export let cursor = 'default';

	export let overflowx = 'visible';
	export let overflowy = 'visible';

	export let position = 'relative';

	export let transition = 'all 150ms';
</script>

<!-- svelte-ignore a11y-no-static-element-interactions -->
<!-- svelte-ignore a11y-mouse-events-have-key-events -->
<!-- svelte-ignore a11y-click-events-have-key-events -->
<div
	on:click
	on:mouseover
	on:mouseleave
	class="column {includeHover ? 'column-hover' : ''}"
	style="overflow-x: {overflowx}; overflow-y: {overflowy}; flex-wrap: {wrap}; box-shadow: {boxshadow}; max-width: {maxwidth}; transition: {transition}; cursor: {cursor}; position: {position}; border: {border}; border-bottom: {borderbottom}; border-top: {bordertop}; border-left: {borderleft}; border-right: {borderright}; border-radius: {borderradius}; align-items: {alignitems}; justify-content: {justifycontent}; gap: {gap}; flex-grow: {grow}; min-width: {minwidth}; min-height: {minheight}; max-height: {maxheight}; padding: {padding}; margin: {margin}; background: {dark
		? 'rgb(20,20,20)'
		: background};"
>
	<slot />
</div>

<style>
	.column {
		display: flex;
		flex-direction: column;
	}

	.column-hover:hover {
		background: rgb(235, 235, 235) !important;
	}
</style>

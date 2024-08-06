<script lang="ts">
	export let alignitems = 'flex-start';
	export let justifycontent = 'flex-start';
	export let gap = '0';
	export let grow = '1';

	export let minheight = 'none';
	export let maxheight = 'none';
	export let minwidth = 'none';
	export let maxwidth = 'none';

	export let padding = '0 0 0 0';
	export let margin = '0 0 0 0';

	export let background = 'white';
	export let border = 'none';
	export let borderright = 'default';
	export let borderradius = '0';
	export let boxshadow = 'none';

	export let overflowx = 'visible';
	export let overflowy = 'visible';

	export let position = 'relative';

	export let transition = 'all 150ms';
</script>

<div
	class="column"
	style=" background: {background}; transition: {transition}; max-width: {maxwidth}; max-height: {maxheight}; border: {border}; border-right: {borderright}; border-radius: {borderradius}; position: {position}; align-items: {alignitems}; justify-content: {justifycontent}; gap: {gap}; flex-grow: {grow}; min-width: {minwidth}; min-height: {minheight}; padding: {padding}; margin: {margin}; overflow-x: {overflowx}; overflow-y: {overflowy}"
>
	<slot />
</div>

<style>
	.column {
		display: flex;
		align-items: flex-start;
		justify-content: flex-start;

        flex-direction: column;
	}
</style>

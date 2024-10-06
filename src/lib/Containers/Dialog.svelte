<script lang="ts">
	export let display = false;
	export let dark = false;

	export let overflow = 'hidden';

	export function openDialog(): void {
		display = true;
	}
	export function closeDialog(): void {
		display = false;
	}

	export let position = 'absolute';
	export let align = 'center';
	export let overflowWrapper = 'hidden';
	export let minheight = '100vh';

	export let minwidth = '100vw';

	export let background = 'white';

	import Card from './Card.svelte';
	import Row from './Row.svelte';
</script>

<div
	style="z-index: 15; overflow: {overflowWrapper}; position: {position}; top: 0; left: 0; min-width: {minwidth}; width: 100%; min-height: {minheight}; height: 100%; flex-grow: 1; transform: scale({display
		? '1'
		: '0'}); transition: all 0; background: rgba(0,0,0,0.25); border-radius: {display
		? '0'
		: '100%'}; display: flex; align-items: {align}; justify-content: center;"
>
	<Card
		{dark}
		direction="column"
		gap="25px"
		overflowx={overflow}
		overflowy={overflow}
		borderradius="5px"
	>
	<slot />
	</Card>
</div>
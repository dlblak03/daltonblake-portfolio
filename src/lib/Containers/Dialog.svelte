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
	export let minheight = 'calc(100vh - 40px)';

	export let minwidth = 'calc(100vw - 40px)';

	export let background = 'white';

	import Card from './Card.svelte';
	import Row from './Row.svelte';
</script>

<div
	style="padding: 20px 20px; z-index: 15; overflow: {overflowWrapper}; position: {position}; top: 0; left: 0; min-width: {minwidth}; width: calc(100% - 40px); min-height: {minheight}; height: calc(100% - 40px); flex-grow: 1; transform: scale({display
		? '1'
		: '0'}); transition: all 150ms; background: rgba(0,0,0,0.5); border-radius: {display
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
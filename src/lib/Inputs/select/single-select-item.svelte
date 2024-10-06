<script lang="ts">
	export let value = '';
	let active = false;

</script>


<!-- svelte-ignore a11y-no-static-element-interactions -->
<!-- svelte-ignore a11y-click-events-have-key-events -->
<div
	class="select-item {active ? 'select-item-active' : ''}"
	style="display: flex; padding: 15px; cursor: pointer;"
	on:click={async () => {
        active = !active;
	}}

	on:click
>
	<slot />
</div>

<style>
	.select-item:hover {
		background: rgb(235, 235, 235);
	}

	.select-item:not(:last-child) {
		border-bottom: solid 1px #e2e2e2;
	}

	.select-item-active {
		background: var(--primary);
	}

	.select-item-active {
		background: var(--primary) !important;
		color: white;
	}

	.select-item:first-child:not(:last-child) {
		border-radius: 5px 5px 0 0;
	}

	.select-item:last-child:not(:first-child) {
		border-radius: 0 0 5px 5px;
	}

	.select-item:last-child:first-child {
		border-radius: 5px;
	}
</style>

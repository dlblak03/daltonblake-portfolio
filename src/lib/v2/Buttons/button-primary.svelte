<script lang="ts">
	export let disabled = false;
	export let inverse = false;

	export let width = 'fit-content';
	export let minheight = 'fit-content';

	export let margin = '0 0 0 0';

	export let boxshadow = 'rgba(0, 0, 0, 0.25) 0px 3px 3px 0px';
</script>

<button
	class="primary-button"
	style="
	width: {width};

	margin: {margin};
	min-height: {minheight};

	box-shadow: {boxshadow};
"
	class:disabled
	class:inverse
	on:click
>
	<slot />
</button>

<style>
	.primary-button {
		display: flex;
		align-items: center;
		justify-content: center;
		gap: 15px;

		height: 50px;
		width: fit-content;

		padding: 0 20px;

		outline: none;
		border: none;
		border-radius: 5px;
		background: var(--primary);

		font-size: 16px;
		font-weight: 500;
		cursor: pointer;
		color: white;

		transition: all 300ms;
	}
</style>

<script lang="ts">
	export let disabled = false;
	export let inverse = false;
	export let dark = false;

	export let width = 'fit-content';
	export let minheight = 'fit-content';

	export let margin = '0 0 0 0';

	export let boxshadow = 'rgba(0, 0, 0, 0.25) 0px 3px 3px 0px';
</script>

<button
	class="primary-button {dark ? "dark" : "light"}"
	style="
	width: {width};

	margin: {margin};
	min-height: {minheight};

	color: {dark ? 'var(--darktext)' : 'var(--primary)'};

	background: {dark ? 'transparent' : 'transparent'};
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
		border: solid 2px;
		border-color: transparent;
		border-radius: 5px;

		font-size: 16px;
		font-weight: 500;
		cursor: pointer;

		transition: all 150ms;
	}

	.dark:hover {
		border-color: var(--darktext) !important;
	}

	.light:hover {
		border-color: var(--primary) !important;
	}
</style>

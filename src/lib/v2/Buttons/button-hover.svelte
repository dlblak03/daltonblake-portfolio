<script lang="ts">
	export let dark = false;

	export let disabled = false;
	export let inverse = false;

	export let width = 'fit-content';
	export let height = '50px';

	export let margin = '0 0 0 0';

	export let background = 'white';
	export let border = 'none';
	
	export let whitelabel = false;
	export let primarycolor = '#540000'
</script>

<button
	class="hover-button"
	style="
	width: {width};
	height: {height};

	margin: {margin};

	background: {dark ? whitelabel ? primarycolor : 'var(--primary)' : background};
	border: {border};
	color: {dark ? 'var(--darktext)' : whitelabel ? primarycolor : 'var(--primary)'}
"
	class:disabled
	class:inverse
	on:click
>
	<slot />
</button>

<style>
	.hover-button {
		display: flex;
		align-items: center;
		justify-content: center;
		gap: 15px;

		height: 50px;
		width: fit-content;

		padding: 0 20px;

		outline: none;
		border-radius: 5px;
		box-shadow: none;

		font-size: 16px;
		font-weight: 500;
		cursor: pointer;

		transition: all 150ms;
	}

	.hover-button:hover {
		box-shadow: rgba(0, 0, 0, 0.25) 0px 3px 3px 0px;
	}
</style>

<script lang="ts">
	export let color = 'default';

	export let letterspacing = 'default';
	export let textalign = 'start';
</script>

<h2 style="color: {color}; letter-spacing: {letterspacing}; text-align: {textalign};"><slot /></h2>

<style>
	h2 {
		display: flex;

		height: 50px;
		width: fit-content;

		margin: 0;

		font-size: 26px;
		font-weight: 500;

		transition: all 150ms;
	}
</style>

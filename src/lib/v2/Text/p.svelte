<script lang="ts">
  export let color = 'default'
  export let fontsize = '16px'
  export let fontweight = '400'
</script>

<p style="color: {color}; font-size: {fontsize}; font-weight: {fontweight};"><slot /></p>

<style>
	p {
		display: flex;

		width: fit-content;

		padding: 0;
		margin: 0;

		transition: all 300ms;
	}
</style>

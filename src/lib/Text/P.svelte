<script lang="ts">
  export let color = 'default'
  export let fontsize = '16px'
  export let fontweight = '400'

  export let letterspacing = "default"
  export let textalign = 'start'

  export let textdecoration = 'none'
</script>

<p style="color: {color}; font-size: {fontsize}; font-weight: {fontweight}; letter-spacing: {letterspacing}; text-align: {textalign}; text-decoration: {textdecoration}"><slot /></p>

<style>
	p {
		display: flex;

		width: fit-content;

		padding: 0;
		margin: 0;

		transition: all 150ms;
	}
</style>

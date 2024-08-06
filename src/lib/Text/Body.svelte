<script lang="ts">
	export let height = 'auto';
	export let width = 'auto';
	export let size = '14px';
    export let color = '#222';
	export let spacing = '0.03rem';
	export let lineheight = 'default';
	export let weight = 'initial';
	export let align = 'left';
</script>

<p style="font-size: {size}; height: {height}; width: {width}; color: {color}; letter-spacing: {spacing}; transition: all 300ms; line-height: {lineheight}; font-weight: {weight}; text-align: {align}">
	<slot />
</p>

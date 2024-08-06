<script lang="ts">
	export let height = 'auto';
	export let width = 'auto';
	export let size = '18px';
    export let color = '#222';
    export let weight = '500';
	export let grow = '0';
	export let align = 'left';
	export let padding = '0';
</script>

<h style="font-size: {size}; height: {height}; width: {width}; color: {color}; font-weight: {weight}; letter-spacing: 0.03rem; transition: all 300ms; flex-grow: {grow}; text-align: {align}; padding: {padding}">
	<slot />
</h>

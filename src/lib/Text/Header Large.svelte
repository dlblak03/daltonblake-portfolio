<script lang="ts">
	export let height = 'auto';
	export let width = 'auto';
	export let size = '32px';
    export let color = '#222';
    export let weight = '400';
</script>

<h style="font-size: {size}; height: {height}; width: {width}; color: {color}; font-weight: {weight}; letter-spacing: 0.2rem; transition: all 300ms;">
	<slot />
</h>

<script lang="ts">
	export let height = 'auto';
	export let width = 'auto';
	export let size = '12px';
	export let color = '#222';
</script>

<p style="font-size: {size}; height: {height}; width: {width}; letter-spacing: 0.03rem; color: {color}">
	<slot />
</p>

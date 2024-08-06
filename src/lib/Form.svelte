<script lang="ts">
	export let method = 'POST';
    export let action = '';
</script>

<form method="{method}" style="width: 100%;" action="{action}">
    <slot />
</form>
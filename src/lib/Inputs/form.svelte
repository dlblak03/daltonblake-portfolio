<script lang="ts">
	export let method = "";
    export let action = "";

    export let gap = "0";

	import { enhance } from '$app/forms';
</script>

<form
	method={method}
	action={action}
	style="display: flex; flex-direction: column; width: 100%; gap: {gap};"
	use:enhance
	on:submit
><slot/></form>

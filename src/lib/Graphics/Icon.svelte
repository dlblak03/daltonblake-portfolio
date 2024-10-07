<script lang="ts">  
	export let size = "";
    export let icon = "";
    export let color = "default";

    export let margin = "0 0 0 0";
</script>

<i style="color: {color}; margin: {margin}; transition: all 150ms;" class="fa-light {icon} {size}"></i>
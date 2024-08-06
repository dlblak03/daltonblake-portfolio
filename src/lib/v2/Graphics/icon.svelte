<script lang="ts">  
	export let size = "";
    export let icon = "";
    export let color = "default";

    export let marginleft = "0";
</script>

<i style="color: {color}; margin-left: {marginleft}; transition: all 150ms;" class="fa-sharp fa-light {icon} {size}"></i>
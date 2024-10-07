<script lang="ts">
    export let color = 'default'

	export let letterspacing = "default"
	export let textalign = "start"
</script>

<h3 style="color: {color}; letter-spacing: {letterspacing}; text-align: {textalign};"><slot/></h3>

<style>
	h3 {
        display: flex;

        width: fit-content;

        margin: 0;

        font-size: 18px;
		font-weight: 500;
		
		transition: all 150ms;
    }
</style>
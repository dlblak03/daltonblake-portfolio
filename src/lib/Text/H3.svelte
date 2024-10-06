<script lang="ts">
    export let color = 'default'

	export let letterspacing = "default"
	export let textalign = "start"
</script>

<h3 style="color: {color}; letter-spacing: {letterspacing}; text-align: {textalign};"><slot/></h3>

<style>
	h3 {
        display: flex;

		height: 50px;
        width: fit-content;

        padding: 20px 20px;
        margin: 0;

        font-size: 24px;
		font-weight: 500;
		
		transition: all 300ms;
    }
</style>
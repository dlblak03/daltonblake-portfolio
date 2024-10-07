<script lang="ts">
	export let letterspacing = "default"
    export let color = 'default'
    export let textalign = 'start'
</script>

<h1 style="color: {color}; letter-spacing: {letterspacing}; text-align: {textalign};"><slot/></h1>

<style>
	h1 {
        display: flex;

		height: 50px;
        width: fit-content;

        padding: 20px 20px;
        margin: 0;

        font-size: 32px;
		font-weight: 500;
		
		transition: all 150ms;
    }
</style>
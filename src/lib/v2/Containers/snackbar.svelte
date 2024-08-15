<script lang="ts">
	export let display = false

    export let minwidth = 'auto'

    export function openSnackbar(): void { display = true }
    export function closeSnackbar(): void { display = false }
    import Card from "./cardtwo.svelte";
	import Row from "./row.svelte";
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<div style="z-index: 100; position: absolute; bottom: 0; left: 0; min-width: 100vw; width: 100vw; min-height: 150px; height: 150px; transform: scale({display ? '1' : '0'}); transition: all 150ms; background: transparent; border-radius: {display ? '0' : '100%'}; display: flex; align-items: center; justify-content: center;">
    <Card direction="column" minheight="100px" minwidth="{minwidth}">
        <Row>
            <slot/>
        </Row>
    </Card>
</div>
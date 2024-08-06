<script lang="ts">  
    export let message = ""
    export let scale = "1"
    export let dark = false

    import Header from '$lib/Text/Header.svelte';
	import Card from './Card.svelte';
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<div style="position: absolute; width: 100%; height: calc(100% - 40px); auto; background: rgba(0,0,0,0.50); bottom: 0; overflow-y: auto; justify-content: center; display: flex; transition: all 100ms; transform: scaleY({scale}); padding: 20px 0; z-index: 100;" on:click>
    <Card maxwidth="none" dark={dark} height="fit-content" marginbottom="160px" margintop="80px">
        <slot></slot>
    </Card>
</div>

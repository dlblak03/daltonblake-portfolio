<script lang="ts">  
	export let gap = "0";
    export let align = "start";
    export let justify = "start";
    export let height = "auto";
    export let width = "auto";
    export let grow = "0";
    export let padding = "0 0";
    export let marginleft = "0";
    export let marginright = "0";
    export let margintop = "0";
    export let marginbottom = "0";
    export let background = "transparent";
    export let cursor = "default";
    export let id = "";
    export let border = "none";
    export let borderradius = "0";
    export let zindex = "1";
    export let wrap = "initial";
    export let overflowx = "default";
    export let overflowy = "default";
    export let minheight = "auto";
    export let rowgap = "0";
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<div on:click id="{id}" style="min-height: {minheight}; overflow-x: {overflowx}; overflow-y: {overflowy}; z-index: {zindex}; display: flex; border-radius: {borderradius}; border: {border}; cursor: {cursor}; position: relative; background: {background}; gap: {gap}; row-gap: {gap}; column-gap: {gap}; align-items: {align}; justify-content: {justify}; height: {height}; width: {width}; flex-grow: {grow}; padding: {padding}; margin-left: {marginleft}; margin-right: {marginright}; margin-top: {margintop}; margin-bottom: {marginbottom}; flex-wrap: {wrap}; row-gap: {rowgap};">
	<slot />
</div>

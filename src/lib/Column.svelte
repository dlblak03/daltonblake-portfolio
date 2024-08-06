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
    export let background = "default";
    export let cssclass = "";
    export let zindex = "1";
    export let minheight = "fit-content";
    export let minwidth = "initial";
    export let maxwidth = "initial";
    export let border = "none";
    export let borderradius = "0";
    export let cursor = "default";
    export let maxheight = "none";
    export let overflowy = "visible";
    export let overflowx = "visible";
</script>

<div class={cssclass} style="overflow-x: {overflowx}; overflow-y: {overflowy}; overflow-x: visible; position: relative; z-index: {zindex}; border-radius: {borderradius}; border: {border}; cursor: {cursor}; display: flex; flex-direction: column; background: {background}; gap: {gap}; align-items: {align}; justify-content: {justify}; height: {height}; min-height: {minheight}; max-height: {maxheight}; width: {width}; min-width: {minwidth}; max-width: {maxwidth}; flex-grow: {grow}; padding: {padding}; margin-left: {marginleft}; margin-right: {marginright}; margin-top: {margintop}; margin-bottom: {marginbottom};">
	<slot />
</div>
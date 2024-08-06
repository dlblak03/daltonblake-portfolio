<script lang="ts">  
	export let gap = "0";
    export let align = "start";
    export let justify = "start";
    export let height = "100%";
    export let width = "100%";
    export let grow = "0";
    export let padding = "0 0";
    export let marginleft = "0";
    export let marginright = "0";
    export let margintop = "0";
    export let marginbottom = "0";
    export let background = "white";
    export let color = "default";
    export let bordercolor = "inherit";
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<div on:click style="display: flex; user-select: none; -moz-user-select: none; -khtml-user-select: none; -webkit-user-select: none; -o-user-select: none; cursor: pointer; border-color: {bordercolor}; border: solid 1px #e1e1e1; border-radius: 50px; min-height: 40px; min-width: 40px; align-items: center; justify-content: center; padding-top: 100%; background: {background}; gap: {gap}; align-items: {align}; justify-content: {justify}; height: {height}; width: {width}; flex-grow: {grow}; padding: {padding}; margin-left: {marginleft}; margin-right: {marginright}; margin-top: {margintop}; margin-bottom: {marginbottom};">
	<div style="width: 95%; height: 100%; display: flex; align-items: center; justify-content: center; color: {color}"><slot /></div>
</div>

<style type="text/css">
    
</style>
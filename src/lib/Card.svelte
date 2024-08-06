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
    export let background = "white";
    export let maxwidth = "default";
    export let dark = false;
    export let shadow = "default"
    export let borderradius = "5px"
</script>

<div class="card" style="border-radius: {borderradius}; box-shadow: {shadow}; display: flex; flex-direction: column; max-width: {maxwidth}; background: {dark ? 'rgb(40,40,40)' : background}; gap: {gap}; align-items: {align}; justify-content: {justify}; height: {height}; width: {width}; flex-grow: {grow}; padding: {padding}; margin-left: {marginleft}; margin-right: {marginright}; margin-top: {margintop}; margin-bottom: {marginbottom};">
	<slot />
</div>

<style type="text/css">
    .card {
        overflow: hidden; position: relative; gap: 20px; padding: 20px 0px; padding-top: 0; display: flex; flex-direction: column; width: 300px; max-width: 300px; box-shadow:0 2.8px 2.2px rgba(0, 0, 0, 0.034), 0 6.7px 5.3px rgba(0, 0, 0, 0.048),0 12.5px 10px rgba(0, 0, 0, 0.06),0 22.3px 17.9px rgba(0, 0, 0, 0.072),0 41.8px 33.4px rgba(0, 0, 0, 0.086),0 100px 80px rgba(0, 0, 0, 0.12); transition: all 300ms;
    }
</style>
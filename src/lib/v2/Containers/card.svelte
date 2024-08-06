<script lang="ts">
    export let dark = false;

    export let display = "flex";
    export let direction = "row";
    export let alignitems = "normal";
    export let aligncontent = "stretch";
    export let alignself = "auto";
    export let justifyitems = "normal";
    export let justifycontent = "stretch";
    export let justifyself = "auto";
    export let gap = "0";

    export let height = "fit-content";
    export let minheight = "50px";
    export let maxheight = "fit-content";
    export let width = "fit-content";
    export let minwidth = "50px";
    export let maxwidth = "fit-content";

    export let padding = "0 0 0 0";
    export let margin = "0 0 0 0";

    export let background = "white";
    export let border = "none";
    export let borderradius = "5px";
    export let boxshadow = "rgba(50, 50, 93, 0.25) 0px 13px 27px -5px, rgba(0, 0, 0, 0.3) 0px 8px 16px -8px";
    export let cursor = "default"

    export let overflowx = "hidden";
    export let overflowy = "hidden";

    export let position = "relative";

    export let transition = "all 300ms";
</script>

<div on:click style="
    display: {display};
    flex-direction: {direction};
    align-items: {alignitems};
    align-content: {aligncontent};
    align-self: {alignself};
    justify-items: {justifyitems};
    justify-content: {justifycontent};
    justify-self: {justifyself};
    gap: {gap};

    height: {height};
    min-height: {minheight};
    max-height: {maxheight};
    width: {width};
    min-width: {minwidth};
    max-width: {maxwidth};

    padding: {padding};
    margin: {margin};

    background: {dark ? 'rgb(40,40,40)' : background};
    border: {border};
    border-radius: {borderradius};
    box-shadow: {boxshadow}; 
    cursor: {cursor};

    overflow-x: {overflowx};
    overflow-y: {overflowy};

    position: {position};

    transition: {transition};
">
	<slot />
</div>
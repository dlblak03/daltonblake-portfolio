<script lang="ts">
    import Header from "./Text/Header.svelte";
    import Icon from "./Icon.svelte";
	import Row from "./Row.svelte";
	import IconImage from "./IconImage.svelte";
  
	export let title = "";
    export let titlecolor = "var(--primary)";
    export let titleiconimage = false;
    export let titleiconimageval = '';

    export let wrap = 'wrap';

    var openCollapsable = false;
</script>

<div style="display: flex; flex-direction: column; width: 100%; border-radius: 5px; overflow: hidden; border: solid 1px var(--primary);">
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <!-- svelte-ignore a11y-no-static-element-interactions -->
    <div on:click on:click={() => { openCollapsable = !openCollapsable }} style="border-bottom: solid 1px var(--primary); padding: 20px; cursor: pointer; border-radius: 5px 5px 0 0; display: flex; align-items: center; gap: 25px;">
        <Row gap="10px" align="center">
            {#if titleiconimage}
                <IconImage name={titleiconimageval} width="50px" height="50px" background="transparent"></IconImage>
            {/if}
            <Header color="{titlecolor}">{title}</Header>
        </Row>
        

        <div style="margin-left: auto;">
            <Icon color={titlecolor} icon="fa-chevron-down" size="fa-lg"></Icon>
        </div>
    </div>

    <div class={openCollapsable ? "open-collapsable" : ""} style="flex-wrap: {wrap}; display: flex; flex-direction: column; max-height: 0; overflow: hidden; transition: all 300ms;">
        <slot></slot>
    </div>
</div>

<style type="text/css">
    .open-collapsable {
        max-height: 5000px !important;
        overflow: visible !important;
    }
</style>
<script lang="ts">
	export let width = '75px';
	export let bordercolor = '#555';
	export let boxshadow = 'none';

	export let position = 'relative';
    export let top = "0px";
    export let left = "0px";

	export let transition = 'all 300ms';

    export let rotate = '0deg';
</script>

<div class="triangle" style="transform: rotate({rotate}); box-shadow: {boxshadow}; border-top: {width} solid transparent; border-bottom: {width} solid transparent; border-right: {width} solid {bordercolor}; position: {position}; transition: {transition}; {position == 'absolute' ? 'top: ' + top + '; left: ' + left + ';' : ''}"></div>

<style>
	.triangle {
        width: 0;
	    height: 0;
	}
</style>

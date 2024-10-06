<script lang="ts">

	export let minheight = 'none';
	export let minwidth = 'none';
    export let maxwidth = 'none';

	export let background = 'white';
	export let border = 'none';
	export let borderradius = '0';
	export let boxshadow = 'none';

	export let position = 'relative';
    export let top = 0;
    export let left = 0;

	export let transition = 'all 300ms';
</script>

<div class="rectangle" style="min-height: {minheight}; min-width: {minwidth}; max-width: {maxwidth}; background: {background}; border-radius: {borderradius}; border: {border}; box-shadow: {boxshadow}; position: {position}; {position == "absolute" ? 'top: ' + top + '; left: ' + left + ';' : ''} transition: {transition};"></div>


<script>
	export let src = 'primary';
    export let alt = 'alt text';
    export let width = "100";
    export let height = "100";
    export let border = "none";
    export let bordersides = "none";
    export let borderradius = "0";
    export let background = "transparent";
    export let id = "";
</script>

<div style="width: {width}; height: {height}; border: {border}; border-radius: {borderradius}; background: {background}; border-left: {bordersides}; border-right: {bordersides}; display: flex;">
    <img id={id} src={src} alt={alt} style="width: 100%; height: 100%; border-radius: {borderradius};">
</div>
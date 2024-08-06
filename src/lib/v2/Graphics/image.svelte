<script lang="ts">
    export let src = 'primary';
    export let alt = 'alt text';

    export let maxwidth = "none"
    export let maxheight = "none"

    export let borderradius = "0";
</script>

<img src={src} alt={alt} style="width: 100%; height: 100%; max-width: {maxwidth}; max-height: {maxheight}; border-radius: {borderradius}; object-fit: cover;">
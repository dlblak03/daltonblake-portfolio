<script lang="ts">
    export let toggle = false;
    export let height = "55px";
    export let background = "var(--primary)"

    export async function getToggleStatus(): Promise<boolean> {
        return toggle;
    }
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<div on:click on:click={() => { toggle = !toggle }} style="display: flex; gap: 40px; padding: 0 20px 0 20px; position: relative; height: {height}; min-width: 75px; align-items: center; margin-right: 20px; cursor: pointer; z-index: 1;">
    <div style="z-index: 2; display: flex; gap: 40px; align-items: center;">
        <slot/>
    </div>
    
    <div style="background: {background}; position: absolute; max-width: 50%; width: 100%; height: 100%; top: 0; left: {toggle ? '50%' : '0'}; border-radius: 5px; z-index: 1; transition: all 150ms;"></div>
</div>
<script lang="ts">  
    export let background = "var(--success)"
    export let message = ""
    export let scale = "0"

    import Header from '$lib/Text/Header.svelte';
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<div on:click class="{scale == '1' ? 'autoshrink open' : 'closed'}" style="height: 100px; position: absolute; width: 100%; background: {background}; bottom: 0; align-items: center; justify-content: center; display: flex; transition: all 300ms; z-index: 100; cursor: pointer; padding-bottom: 20px;">
    <Header color="white">{message}</Header>
    <slot></slot>
</div>

<style type="text/css">
@keyframes autoshrink {
  0% {transform: scale(1);}
  90% {transform: scale(1);}
  100% {transform: scale(0);}
}

.closed {
    transform: scale(0)
}

.open {
    transform: scale(1)
}

.autoshrink {
    animation-name: autoshrink;
  animation-duration: 4s;
  animation-fill-mode: forwards;
}
</style>
